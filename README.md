# OptiChain-Supply-Chain-Analytics
End-to-end FMCG Supply Chain Analytics solution integrating Revenue, Inventory, Procurement, Logistics, Supplier Performance, and Demand Forecast Optimization. Built using Power BI, advanced DAX, and Star Schema modeling with dynamic MAPE-based forecast method selection.
🏭 OptiChain™ – Supply Chain Analytics & Forecast Optimization
🚀 Overview

OptiChain™ is a full-scale Supply Chain Analytics simulation project built for an FMCG enterprise (NovaCare FMCG Ltd) covering operations from Jan 2022 – Dec 2024.

This project integrates:

Revenue Analytics

Inventory Health Monitoring

Supplier Performance Evaluation

Logistics Cost Optimization

Returns & Recovery Analysis

Demand Forecast Accuracy Optimization

The system dynamically selects the most accurate forecasting method based on lowest MAPE.

🎯 Business Objective

To build an integrated decision-support analytics model that:

Improves revenue visibility

Reduces inventory holding cost

Enhances supplier accountability

Controls freight and logistics expenses

Minimizes returns losses

Optimizes demand forecast accuracy

🧩 Data Architecture
📊 Fact Tables (1000+ Records Each)

Sales_Orders

Purchase_Orders

Inventory

Logistics_Shipments

Demand_Forecast

Returns

Supplier_KPIs

📚 Dimension Tables

Product_Master

Supplier_Master

Warehouse_Master

🔹 Implemented using Star Schema data modeling.

📈 Dashboards Developed
📊 Executive Dashboard

Revenue (Cr)

Gross Margin %

Fill Rate %

OTIF %

Forecast Accuracy %

Inventory Value

Logistics Cost

💰 Revenue Dashboard

Revenue by Channel & Region

Gross Profit & Margin

Order Performance & Delay Analysis

📦 Inventory Dashboard

Days of Cover

Stockouts

Expiry Risk

Inventory Health Status

🏭 Supplier Dashboard

OTIF Score

Quality Rejection %

Weighted Score

Supplier Risk Classification

🚚 Logistics Dashboard

Freight Cost

Cost per KM

Damage %

Delivery Delay Days

Cost Efficiency

🔮 Forecast Dashboard

Forecast vs Actual

MAPE %

Bias Analysis

Forecast Accuracy %

Dynamic Best Forecast Method Selection

📊 Forecast Optimization Logic
Best Forecast Method =
VAR SummaryTable =
    ADDCOLUMNS(
        VALUES(Demand_Forecast[Forecast_Method]),
        "AvgMAPE", CALCULATE(AVERAGE(Demand_Forecast[MAPE_Pct]))
    )
RETURN
    MAXX(
        TOPN(1, SummaryTable, [AvgMAPE], ASC),
        Demand_Forecast[Forecast_Method]
    )


Lower MAPE → Higher Accuracy → Best Forecast Model Automatically Selected.
