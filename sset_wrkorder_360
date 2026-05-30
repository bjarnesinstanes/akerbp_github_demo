-- asset_workorder_360.sql
-- Representative curated model for an industrial AI-ready data product
-- Synthetic / anonymised example for portfolio use

with asset_registry as (
    select
        asset_id,
        asset_name,
        asset_class,
        installation_name,
        criticality_level
    from dim_asset_registry
),
work_orders as (
    select
        work_order_id,
        asset_id,
        work_order_type,
        priority_code,
        status_code,
        planned_start_date,
        planned_end_date,
        actual_end_date,
        backlog_flag,
        risk_score
    from fact_work_orders
),
production_context as (
    select
        asset_id,
        production_date,
        production_impact_flag,
        deferred_production_boe,
        uptime_pct
    from fact_asset_production_context
)

select
    a.asset_id,
    a.asset_name,
    a.asset_class,
    a.installation_name,
    a.criticality_level,
    w.work_order_id,
    w.work_order_type,
    w.priority_code,
    w.status_code,
    w.planned_start_date,
    w.planned_end_date,
    w.actual_end_date,
    w.backlog_flag,
    w.risk_score,
    p.production_date,
    p.production_impact_flag,
    p.deferred_production_boe,
    p.uptime_pct,
    case
        when w.backlog_flag = 1 and a.criticality_level in ('HIGH', 'VERY_HIGH') then 'PRIORITISE'
        when w.risk_score >= 0.80 then 'PRIORITISE'
        else 'MONITOR'
    end as maintenance_attention_category
from asset_registry a
left join work_orders w
    on a.asset_id = w.asset_id
left join production_context p
    on a.asset_id = p.asset_id;
