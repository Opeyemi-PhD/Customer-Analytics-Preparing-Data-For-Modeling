# Customer Analytics: Preparing Data for Modeling
## Table of Contents
- [Project Overview](#project-overview)
- [Dataset Description](#dataset-description)
- [Steps Summary](#steps-summary)
- [Conclusions](#conclusions)
---

## Project Overview
A common problem when creating models to generate business value from data is that the datasets can be so large that it can take days for the model to generate predictions. Ensuring that your dataset is stored as efficiently as possible is crucial for allowing these models to run on a more reasonable timescale without having to reduce the size of the dataset.

In this project, I ensured that:
- Columns containing categories with only two factors are stored as Booleans (bool).
- Columns containing integers only are stored as 32-bit integers (int32).
- Columns containing floats are stored as 16-bit floats (float16).
- Columns containing nominal categorical data are stored as the category data type.
- Columns containing ordinal categorical data are stored as ordered categories, and not mapped to numerical values, with an order that reflects the natural order of the column.
  
to achieve a substantial decrease in memory usage.

---

## Dataset Description
The dataset `customer_train.csv` contains approximately 19,160 entries and 14 columns. It includes anonymized student information and indicates whether each student was looking for a new job during the training period.
| Column                   | Description                                                                      |
|------------------------- |--------------------------------------------------------------------------------- |
| `student_id`             | A unique ID for each student.                                                    |
| `city`                   | A code for the city the student lives in.                                        |
| `city_development_index` | A scaled development index for the city.                                         |
| `gender`                 | The student's gender.                                                            |
| `relevant_experience`    | An indicator of the student's work relevant experience.                          |
| `enrolled_university`    | The type of university course enrolled in (if any).                              |
| `education_level`        | The student's education level.                                                   |
| `major_discipline`       | The educational discipline of the student.                                       |
| `experience`             | The student's total work experience (in years).                                  |
| `company_size`           | The number of employees at the student's current employer.                       |
| `company_type`           | The type of company employing the student.                                       |
| `last_new_job`           | The number of years between the student's current and previous jobs.             |
| `training_hours`         | The number of hours of training completed.                                       |
| `job_change`             | An indicator of whether the student is looking for a new job (`1`) or not (`0`). |

---
## Steps Summary
1. Imported the Required Libraries
-  Used **Pandas** for data manipulation and transformation.
  
2. Loaded and Inspected the Dataset
-  Loaded the dataset using `pd.read_csv("customer_train.csv")`.
-  Created a copy of the dataset
-  Displayed the first five rows of the dataset with `head()` function.
-  Obtained a brief summary of the DataFrame using the `info()` function.
3. Inspected and Downcast Column Data Types
-  Checked for the unique values in the `job_change` column
-  converted `job_change` column to `object` data type
-  Used a `for` loop with `if`, `elif`, and `else` conditional statements over each column and converted column(s) of          `object` data yype with only two unique values to `boolean` data type, column(s) of `int64` data type to `int32` data
   type, column(s) of `float64` to `float16`, and columns with the `object` data type with the number of unique values less or more
   than two to `category` data type; to ensure the size of the dataset is reduced and efficiently stored.
4. Inspected and Structured Ordinal Categorical Columns
-  Checked for the unique values in the ordinal categorical columns: `enrolled_university`, `education_level`, `experience`,    `last_new_job`,and `company_size` using the `unique()` function, and set new ordered categories for each column, using
   the `cat` accessor for categorical data, `set_categories()` function, with the following arguments

   i. `new_categories` argument, which contains a list of new categories.

   ii. `ordered` argument which is set to be True, for the new categories tobe ordered.
5. Evaluated and Compared Structural Changes
-  Obtained and compared the brief summary of the original and transformed DataFrame using the `info()` function, to observe
   how the memory usage of the DataFrame decreased substantially from 2.0+ MB down to approximately 400 KB after                transformation.

  ---
  ## Conclusions
  All data manipulation, transformation, and formatting steps were successfully completed.
  The transformed dataset size was reduced to approximately 400 KB, which shows a substantial decrease compared to the size    of the original dataset, and it is stored as efficiently as possible to allow models to run on a more reasonable
  timescale

---
**Author:** _Opeyemi Olanrewaju_  
**Programming Language and Version:** _Python 3.12_
