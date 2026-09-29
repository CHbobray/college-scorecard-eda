# NU Industries Production Planning Optimization

A multi-period **linear programming** model that plans production, inventory, labor, advertising, and shipping for a manufacturer, with scenario analysis, sensitivity analysis, and an integer programming check.

Team project for **MSDS 460: Decision Analytics**, Northwestern University (August 2026).

**Tools:** Python, PuLP, GLPK solver, pandas, Matplotlib, Jupyter

## Problem

NU Industries makes three products (Widgets, Gadgets, Flugels) at two plants over five production periods. It must meet contract demand each period and can buy advertising to create extra demand in the following period. Production draws on two raw materials and on regular and overtime labor, each plant has its own storage limits and costs, and finished goods ship to a distribution center.

**Goal:** choose the production, inventory, labor, advertising, and shipping plan that maximizes total profit while meeting demand and staying within operating limits.

## Model

- **Objective:** maximize profit = sales revenue minus raw material, regular labor, overtime labor, inventory holding, transportation, and advertising costs
- **Decision variables:** units produced and shipped by product, plant, and period; ending inventory; regular and overtime labor hours; extra demand created by advertising
- **Constraints:** inventory balance, demand satisfaction, labor capacity (2,500 regular hours per period at Plant A, 3,800 at Plant B), raw material limits (140,000 lbs of RM1 and 5,000 lbs of RM2 per period), storage limits (70 units at Plant A, 50 at Plant B), a $70,000 advertising budget, and zero ending inventory
- **Verification:** automated checks confirm every constraint holds in the solution

## Results

| Scenario | Maximum profit | Change from baseline |
|---|---|---|
| Baseline | $7,066,036.8 | $0.0 |
| Advertising budget raised to $100,000 | $7,066,036.8 | $0.0 |
| Raw Material 1 +25% | $7,129,332.2 | +$63,295.4 |
| Raw Material 2 +25% | $7,067,094.6 | +$1,057.8 |
| Plant A regular labor +25% | $7,067,734.5 | +$1,697.7 |
| Plant B regular labor +25% | $7,086,595.7 | +$20,558.9 |
| Integer (whole-unit) production | $7,065,782.9 | -$253.9 |

**Key findings**

- **Raw Material 1 is the critical bottleneck.** A small increase captured almost all of the available profit gain, after which other constraints took over.
- **More Plant B labor helps modestly;** more advertising budget does not help at all, because production resources, not demand, are the binding limit.
- **Requiring whole-unit production costs only $254 (0.004%),** so the continuous model's plan is practical as-is.

## Run it

```bash
pip install pulp pandas matplotlib
```

The model uses the **GLPK** solver, which must be installed separately:

- Windows: download from the [GLPK for Windows project](https://sourceforge.net/projects/winglpk/) and add its `w64` folder to your PATH
- macOS: `brew install glpk`
- Linux: `sudo apt install glpk-utils`

Then open `NU_Industries_Production_Optimization.ipynb` in Jupyter and run all cells.

## Files

| File | Description |
|---|---|
| `NU_Industries_Production_Optimization.ipynb` | Model formulation, solution, validation checks, scenarios, sensitivity analysis, and integer programming |
| `NU_Industries_Final_Report.pdf` | Full written report with methodology, results tables, and figures |

## Team

Samin Bahizad, Bobby Hendricks, Deysi Paniagua-Perez, Nathan Stark

[Bobby Hendricks portfolio](https://bobbyhendricks.netlify.app) | [LinkedIn](https://www.linkedin.com/in/bobby-h-143113252/)
