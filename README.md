# CDACL-003 Supply Chain Analysis

A four-page Power BI dashboard that analyses supply chain data across sales, inventory, suppliers, logistics, manufacturing and quality.

## Aim

Turn raw supply chain data into clear comparisons that show:

- which products and locations drive sales
- how stock and availability line up with demand
- how suppliers perform on volume, lead time and manufacturing cost
- which carriers and transport modes cost the most
- where defects are highest

## Dataset

The analysis uses a main table named `supply_chain_data` and a separate `Supplier_Performance` table. Fields include product type, location, supplier name, shipping carrier, transportation mode, revenue, products sold, stock levels, availability, lead times, shipping cost, manufacturing cost, manufacturing lead time and defect rate.

The data has no date column, so the project does not include time-series trends.

## What was done

1. Reviewed the project brief and identified the supply chain dimensions to analyse.
2. Imported the CSV data into Power BI.
3. Checked data types, validity, duplicates and unique values in Power Query, and applied Trim and Clean.
4. Created DAX measures for revenue, products sold, stock, availability, suppliers, lead time, shipping, manufacturing and defect rate. Example:
   `Total Revenue = SUM(supply_chain_data[Revenue generated])`
5. Built four report pages with 15 KPI cards, 19 charts and 9 slicers.
6. Tested every slicer. The supplier slicer first failed to filter the KPI, so it was rebuilt using `Supplier name` from `supply_chain_data`, after which it worked correctly.
7. Wrote a detailed report and a presentation summarising the findings.

## Dashboard pages

1. **Supply Chain Overview:** revenue, products sold, product count, supplier count, average lead time and average defect rate, with comparisons by product type. Slicers: product type, location.
2. **Product and Inventory:** products sold, stock levels and availability by product type and location. Slicers: product type, availability.
3. **Supplier and Logistics:** supplier volume and lead time, shipping cost by carrier and by transport mode, lead time by mode. Slicers: supplier name, shipping carrier, transportation mode.
4. **Manufacturing and Quality:** manufacturing cost, manufacturing lead time and defect rate by product type, supplier and transport mode. Slicers: product type, supplier name.

## Key KPIs

- Total revenue: 577.60K
- Total products sold: 46K
- Total products: 100
- Total suppliers: 5
- Average lead time: 15.96
- Average defect rate: 2.28

## Outcomes

- **Sales:** Skincare is the top product type with 20.7K units sold, about 45% of the total. Kolkata is the top location at 12.8K units, 2.4 times Bangalore at 5.4K.
- **Inventory:** Haircare has the highest stock (1,644) but the lowest availability (43 against 51 for skincare and cosmetics).
- **Suppliers:** Supplier 1 and Supplier 2 lead on volume (11.1K each). Supplier 4 has the longest lead time (17.00), the highest manufacturing cost (63) and the lowest volume (7.2K).
- **Logistics:** Carrier B has the highest shipping cost (237), about 52% above Carrier A (156). Road has the largest cost share (28.97%) and Sea the smallest (15.23%).
- **Quality:** Haircare has the highest defect rate (2.5) and the longest manufacturing lead time (17.1). Road has the highest defect rate by transport mode (2.62) and Air the lowest (1.82).

These findings describe patterns in the dashboard. They show where to investigate, not what caused each result.

## Recommendations

1. Run a root-cause review of haircare defects (process settings, material batches, inspection and rework records).
2. Review Supplier 4 on cost, lead time and quality before changing supplier allocation.
3. Compare Road and Carrier B costs against shipment count, weight, distance and service level.
4. Check haircare stock against sales speed and replenishment lead time.
5. Study why Kolkata sells the most and Bangalore the least.
6. Track the same KPIs at regular intervals.

## Limitations

- Currency, units for lead time, availability, defect rate and stock, and the reporting period are not stated in the dashboard, so they are not assumed here.
- Shipping cost totals are not adjusted for shipment count, weight or distance.
- The supplier volume chart is titled "Supplier-wise Products Supplied" but uses the Total Products Sold measure.

## Tools

- Power BI Desktop (data modelling, DAX, dashboard design)
- Power Query (data preparation)

## Repository contents

- `CDACL-003_Supply_Chain_Dashboard.pbix`: the Power BI dashboard file
- `CDACL-003_Supply_Chain_Report.pdf`: detailed written report
- `CDACL-003_Supply_Chain_Presentation.pptx`: project presentation
- `dashboard_screenshot_1.png`, `dashboard_screenshot_2.png`, `dashboard_screenshot_3.png`: dashboard screenshots

## How to use

Open the `.pbix` file in Power BI Desktop and use the slicers on each page to filter by product type, location, supplier, carrier or transport mode.
