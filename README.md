# Customer-Analytics-Preparing-Data-For-Modeling
## Table of Contents
- Project Overview
- Dataset Description
- Steps Summary
- Conclusions 
---

## Project Overview
A common problem when creating models to generate business value from data is that the datasets can be so large that it can take days for the model to generate predictions. Ensuring that your dataset is stored as efficiently as possible is crucial for allowing these models to run on a more reasonable timescale without having to reduce the size of the dataset.

In this project, I ensured that:
- Columns containing categories with only two factors are stored as Booleans (bool).
- Columns containing integers only are stored as 32-bit integers (int32).
- Columns containing floats are stored as 16-bit floats (float16).
- Columns containing nominal categorical data are stored as the category data type.
- Columns containing ordinal categorical data are stored as ordered categories, and not mapped to numerical values, with an order that reflects the natural order of the column.
- The DataFrame is filtered to only contain students with 10 or more years of experience at companies with at least 1000 employees, as their recruiter base is suited to more experienced professionals at enterprise companies.
  
to obtain substantial decrease in memory usage.

---

## Dataset Description
The dataset `customer_train.csv` contains about 19,160 entries and 14 columns, it contains anonymized student information, and whether they were looking for a new job or not during training
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
