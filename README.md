# COMP5310 Assignment 1

This repository contains the complete analysis for COMP5310 Assignment 1. The notebook compares three candidate datasets, defines the hotel-cancellation stakeholder problem, audits and cleans the selected hotel dataset, and performs decision-focused exploratory data analysis.

## Project structure

Keep the following structure unchanged so that all relative paths resolve correctly:

```text
COMP5310-Assignment-1/
├── Assignment1.ipynb
├── README.md
├── data/
│   ├── airline_delay.csv
│   ├── train_occupancy.csv
│   └── hotel_bookings.csv
└── outputs/                  # Created automatically when the notebook runs
    └── hotel_bookings_cleaned.csv
```

The raw CSV files are inputs and must not be modified. The notebook creates the `outputs/` directory when necessary.

## Dependencies

- Python 3.10 or later
- JupyterLab 4 or Jupyter Notebook 7
- pandas 2.0 or later
- NumPy 1.24 or later
- Matplotlib 3.7 or later
- scikit-learn 1.2 or later
- IPython 8 or later

Install the required packages in a virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
python -m pip install --upgrade pip
python -m pip install jupyterlab pandas numpy matplotlib scikit-learn ipython
```

## Run instructions

1. Place the three source CSV files in `data/` using the exact filenames shown above.
2. Open a terminal in the project root—the folder containing `Assignment1.ipynb`.
3. Start Jupyter with `jupyter lab`.
4. Open `Assignment1.ipynb`.
5. Select **Restart Kernel and Run All Cells**. Run every cell once, from top to bottom; do not run later sections independently.
6. Confirm that the final validation cell completes without an assertion error and that `outputs/hotel_bookings_cleaned.csv` is created.

For a command-line reproducibility check, run:

```bash
jupyter nbconvert --to notebook --execute Assignment1.ipynb \
  --output Assignment1_executed.ipynb --ExecutePreprocessor.timeout=600
```

## Notebook run order and expected outputs

| Order | Section | Main result |
|---:|---|---|
| 1 | Setup | Imports dependencies, sets seed `5310`, defines relative paths, and creates `outputs/` |
| 2 | Part 1: Comparative analysis | Dataset audits, comparison table, and three comparison charts |
| 3 | Part 2: Stakeholder problem | Decision, research question, target, success criteria, and error costs |
| 4 | Part 3: Data readiness | Quality audit, documented cleaning, validation checks, and cleaned CSV export |
| 5 | Part 4: EDA | Cancellation-rate analyses for lead time, market segment, special requests, and arrival month |
| 6 | Team process | Contribution statement and Week 6 role-review record |

The principal generated file is `outputs/hotel_bookings_cleaned.csv`. Displayed tables and plots remain notebook outputs and are not saved as separate files.

## Reproducibility decisions

- All input and output locations use `pathlib` and relative paths.
- Raw data is loaded once and reused in later sections.
- `RANDOM_SEED = 5310` is applied to Python and NumPy. The current analysis is deterministic, but the fixed seed also protects future steps that introduce sampling or randomised modelling.
- Final assertions verify that no exact duplicates, negative ADR values, or unparsed reservation-status dates remain in the cleaned export.
- Part 3 removes exact duplicates after standardisation. Part 4 uses the same cleaned, deduplicated dataframe so that every EDA result follows the documented data-readiness decisions.
- `is_canceled`, `reservation_status`, and `reservation_status_date` are not used together as predictors; the latter two reveal or follow the outcome.

## Contributions and Week 6 checkpoint

| Team member | Contribution |
|---|---|
| Sia | Parts 1 and 3; Github repository; Report Structure |
| Student author | Parts 2 and 4; reproducibility review and README |


## Troubleshooting

- **`FileNotFoundError`**: check that the notebook is launched from the project root and that all CSV files are inside `data/` with the documented names.
- **Date parsing or style error**: verify that the installed pandas and Matplotlib versions meet the minimum versions above.
- **Unexpected results**: restart the kernel and run all cells in order to remove stale variables from earlier interactive runs.

## Reference:
https://www.youtube.com/watch?v=xbkLZI2V3H4
https://chatgpt.com/share/6a892019-e810-83ec-b98d-d9cf002c362b


