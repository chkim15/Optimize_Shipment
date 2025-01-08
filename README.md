# Optimization Tool for Shipment Quantities

## Problem Statement

In the textile industry, we frequently need to quote prices based on customer product requests and quantities. This process involves multiple factors that make manual optimization difficult. This tool automates finding optimal shipment quantities while considering all constraints.

### Key Considerations

- Container capacity limits (20ft, 40ft, 40hq)
- Product-specific production capacity constraints
- Customer demand requirements
- Profit maximization objective

The tool adjusts quantities from initial customer demands while respecting all constraints and maximizing overall profitability.

## Features

- Optimizes product quantities within container volume constraints
- Handles multiple container sizes (20ft, 40ft, 40hq)
- Respects production capacity limits
- Maintains quantities within ±20% of customer demand
- Maximizes total profit
- Rounds quantities to practical order sizes (thousands)

## Prerequisites

```bash
pip install numpy pandas pulp ipywidgets
```

## Usage

1. Prepare input data file (`box_sizes.xlsx`) with columns:
   - Item
   - Per Box (quantity)
   - Width
   - Length
   - Height
   - Unit Profit

2. Launch Jupyter notebook:
```bash
jupyter notebook OptimizeQ.ipynb
```

3. Enter product details:
   - Select items from dropdown
   - Input demand and capacity
   - Choose container size

4. Run optimization to get recommended quantities

## Technical Details

### Constraints

- Total volume ≤ 90% container capacity
- Production quantity ≤ capacity limit
- Quantity within ±20% of demand
- All quantities rounded to thousands

### Mathematical Model

```
Variables:
xi: production quantity for item i
ci: production capacity for item i
di: demand for item i
vi: volume (CBM) of one box for item i
yi: quantity per box for item i
cv: container volume
pi: unit profit for item i

Maximize: Σ(pi * xi)
Subject to:
- xi ≤ ci
- 0.8di ≤ xi ≤ 1.2di
- Σ(vi * xi/yi) ≤ 0.9cv
```
