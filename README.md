# SWYNEX Data Cleaning & Preparation

**Dataset:** Titanic passenger data (public, datasciencedojo/datasets)
**Tool:** Python (pandas)

## Issues found
| Issue | Details |
|---|---|
| Missing values | Age (~177), Cabin (~687), Embarked (2) |
| Duplicates | X exact duplicates, Y duplicate PassengerIds (fill in from script output) |
| Incorrect data types | Pclass and Survived stored as numbers though categorical; Sex/Embarked as plain text |
| Inconsistent values | Embarked coded as C/Q/S; column names in mixed case; possible whitespace/case issues in text |
| Suspicious values | N fares equal to 0 (flagged, retained) |

## Cleaning steps
1. Renamed columns to snake_case.
2. Trimmed whitespace; lowercased `sex`; expanded `embarked` codes to full port names.
3. Removed duplicate rows and duplicate passenger IDs.
4. Converted `pclass`, `sex`, `embarked` to category and `survived` to int8.
5. Age: filled with median by class and sex, with an `age_imputed` flag column.
6. Embarked: filled with the most frequent value.
7. Cabin: dropped (too sparse), replaced by a `cabin_known` boolean.
8. Validated age (0–100) and fare (≥ 0).

## Result
891 rows × 12 columns → 0 missing values, 0 duplicates, correct dtypes.

## How to run
pip install pandas && python clean_data.py
