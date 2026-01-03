# Operations KPI Dashboard (Manufacturing-Focused)

## Project Overview
This project solves the problem of manual Excel reporting in manufacturing by providing real-time visibility into operations via an interactive Power BI dashboard. It tracks key performance indicators (KPIs) including Throughput, Defect Rate, Cycle Time, Efficiency, Downtime, and Overall Equipment Effectiveness (OEE). The dashboard includes filters for date and department, and an executive summary page.

The dashboard uses Power BI for visualization, SQL for data querying, and Excel for potential data import. Data is assumed to come from a SQL database (e.g., ERP system). For demonstration, sample data is generated using Python.

## Tools
- Power BI: Interactive visuals and filters.
- SQL: Data aggregation and queries.
- Excel: Fallback for data import/export.
- Python: Sample data generation (using pandas and numpy).

## KPIs and Formulas
- **Throughput**: Total units produced (SUM(Units_Produced)).
- **Defect Rate**: (SUM(Defects) / SUM(Units_Produced)) * 100.
- **Cycle Time**: Average actual cycle time (AVG(Cycle_Time)) in minutes.
- **Efficiency**: (SUM(Units_Produced) / SUM(Expected_Output)) * 100.
- **Downtime**: Total downtime (SUM(Downtime)) in minutes.
- **OEE**: Availability * Performance * Quality * 100, where:
  - Availability = (480 - Downtime) / 480
  - Performance = (Units_Produced * Ideal_Cycle_Time) / (480 - Downtime)
  - Quality = (Units_Produced - Defects) / Units_Produced

Assumptions: Planned production time = 480 minutes/day; times in minutes.

## Setup Instructions
1. Run `scripts/generate_data.py` to create `data/sample_data.csv`.
2. Import the CSV into a SQL database (create table `Production_Log` with columns from the CSV).
3. Open Power BI, connect to the SQL database (or import CSV).
4. Use the queries in `sql/queries.sql` for data transformation.
5. Add DAX measures from `powerbi/dax_measures.txt`.
6. Build visuals: Line charts for trends over time, bar charts for by-department, gauges for OEE.
7. Add slicers for Date (range) and Department.
8. Create an Executive Summary page with KPI cards.

## Sample OEE Visualization
Here's a sample bar chart showing average OEE by department from the generated data (note: values >100% due to simulation; adjust in real data).

[Insert rendered chart here in your README if using GitHub features, or link to an image.]

## Business Impact
This dashboard provides real-time insights, reducing reporting time and highlighting bottlenecks like high downtime or low OEE. It's practical and impactful for manufacturing operations.

## License
MIT License.
