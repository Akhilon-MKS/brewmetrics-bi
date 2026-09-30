1. Month-over-Month Growth %

Objective

Calculate the percentage change in Total Sales compared with the
previous month.

Copilot Prompt

I have a Power BI semantic model with these tables:

Fact_Sales:

- date
- sales_amount
- item
- city
- category
- quantity

Dim_Date:

- Date
- Day
- Month
- Month Number
- Year

I already have this measure:

Total Sales =
SUM(Fact_Sales[sales_amount])

Create a DAX measure called MoM Growth % that calculates the percentage
change in Total Sales compared with the previous month. Use
Dim_Date[Date] for the time calculation.

Copilot Initial Suggestion

A possible DAX measure for calculating month-over-month growth is:

```DAX
MoM Growth % =
VAR CurrentSales = [Total Sales]
VAR PreviousSales =
    CALCULATE(
        [Total Sales],
        DATEADD(Dim_Date[Date], -1, MONTH)
    )
RETURN
DIVIDE(
    CurrentSales - PreviousSales,
    PreviousSales
)

### My Correction / Modification

I reviewed the Copilot suggestion against the Power BI data model.
The calculation needs to use the Dim_Date[Date] column for the
time-intelligence calculation and compare the current month's
Total Sales with the previous month's Total Sales.

### Final Measure

```DAX
MoM Growth % =
VAR CurrentSales = [Total Sales]
VAR PreviousSales =
    CALCULATE(
        [Total Sales],
        DATEADD(Dim_Date[Date], -1, MONTH)
    )
RETURN
DIVIDE(
    CurrentSales - PreviousSales,
    PreviousSales
)
2. Running Total Sales
Objective

Calculate cumulative Total Sales over time.

Copilot Prompt

I have a Power BI semantic model with Fact_Sales and Dim_Date tables.

I already have this measure:

Total Sales =
SUM(Fact_Sales[sales_amount])

Dim_Date contains a Date column called Date.

Create a DAX measure called Running Total Sales that calculates
cumulative Total Sales over time using Dim_Date[Date].

Initial AI Suggestion

A possible DAX measure for calculating cumulative sales is:

Running Total Sales =
CALCULATE(
    [Total Sales],
    FILTER(
        ALL(Dim_Date[Date]),
        Dim_Date[Date] <= MAX(Dim_Date[Date])
    )
)
My Correction / Modification

I reviewed the suggested calculation and verified that the measure
needs to accumulate Total Sales for all dates up to the current date
in the filter context.

I used Dim_Date[Date] so that the date dimension controls the
running total.

Final Measure
Running Total Sales =
CALCULATE(
    [Total Sales],
    FILTER(
        ALL(Dim_Date[Date]),
        Dim_Date[Date] <= MAX(Dim_Date[Date])
    )
)
Testing

The measure was tested using Date, Total Sales, and Running Total Sales.

The Running Total Sales value increases cumulatively as the date
progresses.

3. Product Rank
Objective

Rank products based on Total Sales from highest sales to lowest sales.

Copilot Prompt

I have a Power BI semantic model with a Dim_Product table and
Fact_Sales table.

Dim_Product contains:

item
category

I already have this measure:

Total Sales =
SUM(Fact_Sales[sales_amount])

Create a DAX measure called Product Rank that ranks products based
on Total Sales.

Use RANKX and rank the products from highest Total Sales to lowest
Total Sales.

Use Dim_Product[item] as the product field.

Initial AI Suggestion

A possible DAX measure for ranking products based on Total Sales is:

Product Rank =
RANKX(
    ALL(Dim_Product[item]),
    [Total Sales],
    ,
    DESC,
    DENSE
)
My Correction / Modification

I reviewed the suggested ranking calculation against the Power BI
data model.

I verified that Dim_Product[item] is the product field and that
Total Sales should be used as the expression for ranking.

I used RANKX with descending order so that the product with the
highest Total Sales receives rank 1.

The DENSE option was used so that tied products receive the same rank
without gaps in the ranking sequence.

Final Measure
Product Rank =
RANKX(
    ALL(Dim_Product[item]),
    [Total Sales],
    ,
    DESC,
    DENSE
)
Testing

The measure was tested using a table containing:

Dim_Product[item]
Total Sales
Product Rank

The products are ranked according to their Total Sales.

4. Average Transaction Value
Objective

Calculate the average revenue generated per transaction.

Copilot Prompt

I have a Power BI semantic model with Fact_Sales.

Fact_Sales contains:

sale_id
sales_amount

I already have this measure:

Total Sales =
SUM(Fact_Sales[sales_amount])

Create a DAX measure called Average Transaction Value that calculates
the average revenue per transaction using Total Sales divided by the
distinct number of sale_id values.

Use DIVIDE to safely handle division by zero.

Initial AI Suggestion

A possible DAX measure for calculating average transaction value is:

Average Transaction Value =
DIVIDE(
    [Total Sales],
    DISTINCTCOUNT(Fact_Sales[sale_id])
)
My Correction / Modification

I reviewed the suggested calculation against the Power BI data model.

I verified that sale_id identifies the transactions and that
DISTINCTCOUNT should be used to count the number of unique
transactions.

I also verified that DIVIDE is appropriate because it safely handles
division by zero.

Final Measure
Average Transaction Value =
DIVIDE(
    [Total Sales],
    DISTINCTCOUNT(Fact_Sales[sale_id])
)
Testing

The measure was tested using the overall sales data and can also be
analyzed by dimensions such as city, product, and date.