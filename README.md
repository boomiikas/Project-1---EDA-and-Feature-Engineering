# 📝 Separate Names from ID – Data Cleaning Task

## 📌 Overview
This small project demonstrates a **data cleaning** task where the `id` column in a CSV file contains both a numeric ID and a name combined (e.g., `12345Johnny`).  
The goal is to split these into **two separate columns**:
- `ID` – Numeric identifier
- `First_Name` – Person's first name

---

## 📂 Dataset
**File:** `separate_names.csv`  
**Original Structure:**
| id           |
|--------------|
| 12345Johnny  |
| 93829Sally   |
| 20391Larry   |

---

## 🔍 Steps Performed
1. Read the CSV file using **Pandas**
2. Extract the numeric part as `ID`
3. Extract the alphabetical part as `First_Name`
4. Save the cleaned dataset to a new CSV file

---

## 🛠️ Code Example
```python
import pandas as pd

# Load data
df = pd.read_csv("separate_names.csv")

# Split into numeric ID and name
df['ID'] = df['id'].str.extract(r'(\d+)')
df['First_Name'] = df['id'].str.extract(r'([A-Za-z]+)')

# Save cleaned file
df.to_csv("separated_output.csv", index=False)
