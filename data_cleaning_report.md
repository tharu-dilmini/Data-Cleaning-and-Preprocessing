
# Data Cleaning Report: Hotel Booking Demand Dataset

##  Dataset Overview
- **Source**: Kaggle – Hotel Booking Demand Dataset
- **Rows**: 119,390
- **Columns**: 32
- **Duration**: July 2015 to August 2017
- **Data Types**: Mixed (numerical, categorical, datetime)

---

## Initial Inspection
- Checked shape, data types, and sample rows
- Identified missing values in: `children`, `agent`, `company`, `country`
- Found 37 duplicate records
- Detected outliers in `adr`, `lead_time`
- Identified invalid rows with 0 total guests

---

##  Data Cleaning Steps

### 1. Handling Missing Values
| Column     | Strategy               |
|------------|------------------------|
| `children` | Filled with 0          |
| `agent`    | Filled with 0          |
| `company`  | Filled with 0          |
| `country`  | Filled with mode or 'Unknown' |

### 2. Duplicate Removal
- Removed 37 exact duplicates
- Removed near-duplicates by ignoring time-based variations

### 3. Outlier Treatment
- Used IQR and Z-Score methods
- Capped extreme values in `adr`, `lead_time`, and guest counts

### 4. Inconsistency Fixes
- Standardized categorical values like `country` and `meal`
- Parsed and validated date fields (arrival and reservation dates)
- Removed rows where `adults + children + babies == 0`

### 5. Data Integrity Checks
- Ensured total guests > 0
- Validated arrival dates between Jan 2015 and Sep 2017
- Checked that all categorical fields have valid values

---

## Results

| Metric                    | Before        | After         |
|---------------------------|---------------|---------------|
| Rows                      | 119,390       | 118,772       |
| Missing Values            | Present       | 0             |
| Duplicate Records         | 37            | 0             |
| Outlier Values            | Several       | Capped        |
| Invalid Guest Rows        | 180           | 0             |
| Final Format              | CSV Exported  | Ready       |

---

## Assumptions Made
- Missing `children`, `agent`, and `company` imply zero
- Country missing values can be 'Unknown'
- ADR outliers reflect errors or rare prices
- 0 guests means invalid booking and was removed


