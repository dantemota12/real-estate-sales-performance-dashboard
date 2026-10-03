# Real Estate Sales Performance Dashboard

Interactive Tableau dashboard that evaluates the commercial performance of a real estate company: revenue, profitability, growth, sales channels, customer segments and customer retention through cohort analysis.

🔗 **[View the live dashboard on Tableau Public](https://public.tableau.com/app/profile/dante.alvarado/viz/Tablero_Inmobiliario_Andes_Capital/TendenciadeVentas)**

## Business Questions

- What is the total revenue, number of properties sold, average sale price and total commission?
- Which property type, sales channel and customer segment generate the most revenue?
- How do sales evolve over time? Is the business growing year over year?
- Do customers come back to buy after their first purchase? Which cohorts perform best?

## Dashboard Structure

### 1. Executive Overview
- **KPIs:** Total Revenue, Number of Sales, Average Ticket, Total Commission
- Sales trend over time
- Revenue by city
- Year-over-year (YoY) growth

### 2. Commercial Analysis
- Revenue by property type
- Revenue by sales channel
- Revenue by customer segment
- Table with conditional formatting (traffic-light colors) to highlight top-performing categories
- Tooltips with share-of-total (%) measures

### 3. Cohort Analysis
- Cohort matrix: rows = cohort month (first purchase), columns = sale month, values = number of sales
- Shows whether customers repurchase and how cohorts compare over time

## Data Model

Star schema with three tables:

- `hecho_ventas_propiedades`: fact table with sales transactions (price, customer, property, channel, date)
- `dim_clientes`: customer information and segmentation
- `dim_propiedades`: property characteristics (type, size, location)

> Table names, column names and category values are in Spanish, as in the original dataset.

## Calculated Fields

- **Base measures:** Total Revenue, Number of Sales, Average Ticket, Total Commission
- **Filter-context measures:** share of revenue by property type, sales channel and customer segment, using `{ FIXED : SUM([Sale Price]) }` LOD expressions in the denominator
- **Time intelligence:** Year to Date (YTD), Previous Year Sales, YoY Growth
- **Cohort fields:** First Purchase per Customer (`FIXED` LOD), Cohort Month, Sale Month

## Data Preparation

- Converted `fecha_venta` to Date format and formatted numeric fields
- Formatted `porcentaje_comision` as a percentage
- Checked for null values in all tables
- Validated that primary keys in `dim_clientes` and `dim_propiedades` have no duplicates

## Key Findings

| Metric | Result |
|---|---|
| Total revenue | $6,012,502,170 |
| Number of sales | 8,500 |
| Average ticket | $707,353 |
| Total commission | $200,627,166 |
| YoY growth (2023 → 2024) | **+11.14%** |

- **Top property type:** House ($2,240,535,304)
- **Top city:** Mexico City ($3,242,231,285)
- **Top sales channel:** Broker ($4,379,990,279)
- **Top customer segment:** First-time buyers ($3,783,579,998)
- Customers acquired in the **March and April** cohorts show the highest repurchase rates.

## Recommendations

1. Prioritize the sale of **houses**, the highest-revenue property type.
2. Strengthen the **broker channel**, which accounts for the largest share of revenue.
3. Implement **retention strategies for first-time buyers** to improve repurchase rates in recent cohorts.

## Tools

Tableau Public · Calculated Fields · LOD Expressions (`FIXED`) · Cohort Analysis · Data Modeling

## Files

- `sprint 11 - cuaderno de jupyter - S11 Estudiante Proyecto InmobiliarioGrupoAndes.ipynb`: project notebook with the data cleaning, modeling and measure requirements, and the executive summary.
- `images/`: screenshots of the dashboard pages.
- [Live dashboard on Tableau Public](https://public.tableau.com/app/profile/dante.alvarado/viz/Tablero_Inmobiliario_Andes_Capital/TendenciadeVentas)
- [Download the Tableau workbook (.twbx) from Google Drive](https://drive.google.com/file/d/1_GFJZyn0b7IzJj3Wll6hvL3sgqLc3sQz/view?usp=sharing)
- [Download the notebook from Google Drive](https://drive.google.com/file/d/1_spCxtGTNRXRXlWaUQjdJup6nPjWNeYJ/view?usp=sharing)
## Author

**Dante Mota**: [GitHub](https://github.com/dantemota12)
