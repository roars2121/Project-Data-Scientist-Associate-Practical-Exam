
# RealAgents House Sales Analysis

This repository contains code and instructions for exploring, cleaning, and modeling the RealAgents house‐sales dataset. You’ll find:

- A description of each column and its cleaning rules  
- Step‐by‐step tasks:  
  1. Counting missing cities  
  2. Producing a cleaned DataFrame  
  3. (Skipped)  
  4. Fitting a baseline price model  

---

## Data Files

- **house_sales.csv**  
  Raw dataset of house sales, used for Task 1 (missing‐city count) and Task 2 (cleaning).

- **train.csv**  
  Training split for modeling (Task 4).

- **validation.csv**  
  Hold‐out split for generating baseline predictions (Task 4).

---

## Column Definitions & Cleaning Rules

| Column         | Type      | Description                                                                                      | Missing‐Value Handling                                                                                          |
|----------------|-----------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| **house_id**   | Nominal   | Unique identifier for each house.                                                                | No missing values possible.                                                                                     |
| **city**       | Nominal   | One of `Silvertown`, `Riverford`, `Teasdale`, `Poppleton`.                                       | Replace missing with `"Unknown"`.                                                                               |
| **sale_price** | Discrete  | Sale price in whole dollars (≥ 0).                                                               | Drop rows with missing sale_price.                                                                               |
| **sale_date**  | Discrete  | Date of last sale (YYYY‐MM‐DD).                                                                  | Replace missing with `2023-01-01`.                                                                              |
| **months_listed** | Continuous | Months on market before sale, rounded to one decimal.                                           | Fill missing with overall mean (rounded to one decimal).                                                        |
| **bedrooms**   | Discrete  | Number of bedrooms (integer ≥ 0).                                                                 | Fill missing with overall mean (rounded to nearest integer).                                                    |
| **house_type** | Ordinal   | One of `Terraced`, `Semi-detached`, `Detached`.                                                  | Fill missing with the most frequent type in the dataset.                                                        |
| **area**       | Continuous| Area in square meters, rounded to one decimal.                                                   | Fill missing with overall mean (rounded to one decimal).                                                        |

---

## Task 1: Count Missing Cities

1. Load **house_sales.csv**.  
2. Count the number of `NaN` or empty entries in the `city` column.  
3. Return a Python integer (or pandas object) named `missing_city` containing that count.


## Task 2: Clean the Dataset

Create a cleaned DataFrame `clean_data` from **house_sales.csv** by applying the rules above:

---

## Task 4: Baseline Price Model

1. Load **train.csv** and **validation.csv**.  
2. Fit a simple baseline (e.g., mean‐price) or regression model on **train.csv**.  
3. Predict sale prices for houses in **validation.csv**.  
4. Return a DataFrame `base_result` with columns:
   - `house_id`  
   - `price` (your predicted sale price)

```python
# Example: baseline = mean price
train = pd.read_csv("train.csv")
val = pd.read_csv("validation.csv")

baseline_price = train["sale_price"].mean()
val["price"] = baseline_price

base_result = val[["house_id", "price"]]
```

---

## Environment & Dependencies

- Python 3.8+  
- pandas  
- scikit‐learn (optional for more advanced baseline models)  

Install via:

```bash
pip install pandas scikit-learn
```

