# Budget Tracker 2026

A command-line Python program that simulates a full year of daily spending, saves it to a CSV file, and lets you explore it through a simple menu. All calculations use NumPy arrays, with no row-by-row loops.

## Features

- Generates 365 days of spending across 9 categories
- Realistic patterns: Food is spent almost daily, Entertainment and Shopping rise on weekends, and Bills fall on the 5th of every month
- Saves and reloads data from `Budget_Tracker2026.csv`
- Menu-driven analysis:
  1. Yearly total for a category (total, daily average, highest-spending day)
  2. Month-wise spending for a category
  3. Full report for a month
  4. Spending on a specific date
  5. Full-year summary with percentage share and most expensive month

## Requirements

- Python 3.8 or later
- NumPy

```bash
pip install numpy
```

## Usage

```bash
python budget_tracker.py
```

The program creates `Budget_Tracker2026.csv` in the current folder, then shows the menu:

```
===== 2026 EXPENSE DATA =====
1. Yearly total for a category
2. Month-wise spending for a category
3. Full report for a month
4. Spending on a specific date
5. Full year summary
0. Exit
```

Enter the number of the option you want. For option 4, use the date format `YYYY-MM-DD` (for example `2026-03-15`).

## Categories

Entertainment, Travel, Shopping, Stationary, Food, Bills, Health, Education, Other

## Data Format

One row per day, one column per category. A value of `0` means nothing was spent.

```
date,Entertainment,Travel,Shopping,Stationary,Food,Bills,Health,Education,Other
2026-01-01,0.0,0.0,1310.45,0.0,231.8,0.0,0.0,0.0,0.0
```

## How It Works

| Step | Function | Description |
|---|---|---|
| 1 | `create_dataset()` | Generates random daily spending using per-category probabilities and average amounts, then saves it as CSV |
| 2 | `load_dataset()` | Reads the CSV into NumPy arrays |
| 3 | Menu loop | Uses boolean masks and axis sums to answer each query |

Helper functions: `ask_int()` (validated number input), `pick_category()`, `pick_month()`.

The random generator uses a fixed seed (`42`), so the same data is produced on every run.

## NumPy Concepts Demonstrated

- Seeded random generation (`default_rng`)
- Boolean masks for filtering by month or day
- Vectorized operations
- Axis operations (`sum(axis=0)`)
- `np.where` and `np.argmax`

## Notes

- The data is simulated, not real expenses.
- The CSV is regenerated and overwritten each time the program starts.
- Date lookup only accepts dates in 2026.

## Possible Improvements

- Use pandas for grouping and named columns
- Add charts with matplotlib
- Let users enter their own expenses instead of random data
acker
