
# Pricing Engine

You need to create a Python script that automatically adjusts product prices based on inventory levels and sales performance. This is essentially a dynamic pricing engine.


## The Goal

The main objective is to optimize product pricing by analyzing:

1.Current stock levels (supply)

2.Recent sales data (demand)

3.Cost price (to maintain profitability)

The system should automatically apply price increases or decreases following specific business rules, ensuring products maintain healthy profit margins.


## RULES:

### 1. Low Stock, High Demand (Highest Priority)

When inventory is below 20 units AND recent sales exceed 30 units
Action: Price increased by 15%


### 2.Dead Stock (Second Priority)

When inventory exceeds 200 units AND no recent sales
Action: Price decreased by 30%


### 3.Overstocked Inventory (Third Priority)

When inventory exceeds 100 units AND recent sales are below 20 units
Action: Price decreased by 10%


### 4.Minimum Profit Constraint (Always Applied)

Ensures new price is at least 20% above cost price
Applied after any of the above rules

## Implementation Details
### Input Files

products.csv: Contains product catalog with SKU, name, current price, cost price, and stock levels
sales.csv: Contains recent sales data with SKU and quantity sold

### Output File

updated_prices.csv: Contains SKU, old price (with $ unit), and new price (with $ unit)

### Processing Logic

1.Data is loaded and merged from both input files

2.Each product is evaluated against the pricing rules in order of precedence

3.Only one rule from Rules 1-3 is applied to each product

4.The minimum profit constraint is always checked

5.Final prices are rounded to 2 decimal places and formatted with currency symbols


## Usage

To run the pricing engine:

```bash
  python pricing_engine.py
```

Ensure both input CSV files are in the same directory as the script.

### Dependencies

-pandas

### Notes

-The script handles missing sales data by treating them as zero sales

-Currency is formatted as USD ($)

-All prices are rounded to 2 decimal places as per standard financial practice

