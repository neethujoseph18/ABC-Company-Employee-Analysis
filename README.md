# ABC Company Employee Data Analysis

## Table of Contents
1. [Project Overview](#project-overview)
2. [Objectives](#objectives)
3. [Tools and Technologies](#tools-and-technologies)
4. [Dataset](#dataset)
5. [Data Preprocessing](#data-preprocessing)
6. [Analysis and Visualisation](#analysis-and-visualisation)
7. [Key Findings](#key-findings)
8. [Data Story](#data-story)
9. [Conclusion](#conclusion)
10. [Limitations](#limitations)
11. [Project Structure](#project-structure)
12. [How to Run the Project](#how-to-run-the-project)

---

## Project Overview

This project analyses ABC Company's employee dataset, consisting of **458 records and 9 columns**, using Python. The objective is to understand employee distribution across teams and positions, analyse age groups and salary expenditure, and identify the relationship between age and salary.

Using Pandas, NumPy, Matplotlib and Seaborn, the project involves data preprocessing, exploratory data analysis and visualisation to identify key workforce trends and insights.

## Objectives

- Inspect and preprocess the dataset, including correcting the `Height` column.
- Determine the distribution of employees across each team and calculate the percentage split relative to the total.
- Analyse employee distribution by position.
- Identify the predominant age group.
- Discover which team and position have the highest salary expenditure.
- Investigate the correlation between age and salary.
- Present findings using appropriate visualisations.

## Tools and Technologies

| Tool | Purpose |
|---|---|
| Python 3 | Programming language |
| Jupyter Notebook | Writing and executing Python code |
| Pandas | Data cleaning, manipulation and analysis |
| NumPy | Numerical operations and random number generation |
| Matplotlib | Data visualisation |
| Seaborn | Statistical data visualisation |

## Dataset

**File:** `ABC Company Dataset.csv`

**Dataset size:** 458 rows × 9 columns.

| Column | Description |
|---|---|
| Name | Employee name |
| Team | Team the employee belongs to |
| Number | Employee identification number |
| Position | Employee playing position |
| Age | Employee age |
| Height | Employee height |
| Weight | Employee weight |
| College | College attended |
| Salary | Employee salary |


## Data Preprocessing

The following preprocessing steps were performed:

1. Loaded the dataset using Pandas `read_csv()`.
2. Inspected the dataset structure, data types and missing values.
3. Checked for duplicate records. No duplicate records were found.
4. Converted the Salary column into numeric format.
5. Replaced the 11 missing Salary values with the mean salary.
6. Replaced the Height column with random integer values between 150 and 180, as required by the project.
7. Created age groups using `pd.cut()`.

### Missing Values

| Column | Missing values |
|---|---:|
| College | 84 |
| Salary | 11 |

The mean salary calculated was approximately **$4,833,969.55**. After mean imputation, the Salary column contained no missing values. The missing College values were retained.

### Preprocessing Code

```python
df["Salary"] = pd.to_numeric(df["Salary"], errors="coerce")
df["Salary"] = df["Salary"].fillna(df["Salary"].mean())

np.random.seed(42)
df["Height"] = np.random.randint(150, 181, size=len(df))
```

## Analysis and Visualisation

### 1. Employee Distribution Across Teams

Employee counts and percentage distribution were calculated using Pandas `groupby()`.

**Key observations:**
- Total teams: 30.
- New Orleans Pelicans has the highest employee count, with 19 employees (4.15%).
- Memphis Grizzlies follows with 18 employees (3.93%).
- Minnesota Timberwolves and Orlando Magic have the lowest employee count, with 14 each (3.06%).
- Most teams have 15 employees (3.28%).

Visualisations: Count Plot and Pie Chart.

### 2. Employee Distribution by Position

The employee count was calculated for each of the five original positions.

| Position | Employees | Percentage |
|---|---:|---:|
| SG | 102 | 22.27% |
| PF | 100 | 21.83% |
| PG | 92 | 20.09% |
| SF | 85 | 18.56% |
| C | 79 | 17.25% |

**Key observation:** SG has the highest representation, while C has the lowest representation.

### 3. Predominant Age Group

Employees were grouped into four age categories.

| Age Group | Employees | Percentage |
|---|---:|---:|
| 18–24 | 154 | 33.62% |
| 25–29 | 182 | 39.74% |
| 30–34 | 90 | 19.65% |
| 35–40 | 32 | 6.99% |

**Key observation:** The predominant age group is 25–29, with 182 employees (39.74%). Employees aged 18–29 account for approximately 73.36% of the workforce.

### 4. Salary Expenditure by Team and Position

A pivot table was created to calculate total salary expenditure across teams and positions. A stacked horizontal bar chart was used to compare the results.

**Key findings after mean imputation:**
- Highest salary expenditure by team: Cleveland Cavaliers (approximately $111.8 million).
- Highest salary expenditure by position: C (approximately $466.4 million).

| Position | Total Salary ($M) |
|---|---:|
| C | 466.4 |
| PG | 466.2 |
| PF | 457.1 |
| SF | 412.9 |
| SG | 411.5 |

**Key observation:** C account for the highest salary expenditure despite having the lowest employee count. However, the difference between C and PG is relatively small, at approximately $0.2 million.

### 5. Correlation Between Age and Salary

Pearson correlation was used to investigate the relationship between employee age and salary.

**Correlation coefficient: 0.211**

**Key observation:** The result indicates a weak positive correlation between age and salary. This suggests that salary tends to increase slightly with age, but age alone does not strongly determine employee salary.

A scatter plot with a regression line was used to visualise the relationship.

## Key Findings

| Analysis | Result |
|---|---|
| Total employees | 458 |
| Total teams | 30 |
| Largest team | New Orleans Pelicans – 19 employees |
| Smallest teams | Minnesota Timberwolves and Orlando Magic – 14 each |
| Most common position | SG – 102 employees |
| Least common position | C – 79 employees |
| Predominant age group | 25–29 – 182 employees |
| Employees aged 18–29 | 73.36% |
| Highest team salary expenditure | Cleveland Cavaliers |
| Highest position salary expenditure | C |
| Age-salary correlation | 0.211 – Weak positive correlation |

## Data Story

The ABC Company dataset consists of 458 employees across 30 teams. The analysis was carried out to understand employee distribution, position-wise representation, age groups, salary expenditure and the relationship between age and salary.

The team-wise analysis shows that the workforce is fairly evenly distributed. New Orleans Pelicans has the highest number of employees, with 19 (4.15%), followed by Memphis Grizzlies with 18 (3.93%). Minnesota Timberwolves and Orlando Magic have the lowest headcount, with 14 employees each (3.06%). Most teams have 15 employees (3.28%).

Regarding positions, SG form the largest group, with 102 employees (22.27%), while C have the lowest representation, with 79 employees (17.25%). The age analysis indicates that the workforce is relatively young, with the 25–29 age group being the largest, consisting of 182 employees (39.74%). Employees aged 18–29 account for approximately 73.36% of the total workforce.

The salary analysis reveals that the Cleveland Cavaliers have the highest total salary expenditure among all teams, while the C position accounts for the highest salary expenditure among the five positions. Finally, the correlation between age and salary is 0.211, indicating a weak positive relationship. This suggests that salary tends to increase slightly with age, but age alone does not strongly determine an employee's salary.

## Conclusion

Overall, ABC Company has a relatively balanced distribution of employees across teams and positions, with a predominantly young workforce. Salary expenditure varies across teams and positions, while the weak positive correlation between age and salary suggests that other factors also influence employee compensation.

## Limitations

- **Mean imputation:** The 11 missing salary values were replaced with the average salary of approximately $4.83 million. This affects total salary expenditure and may influence the correlation analysis.
- **Height column:** The original Height values were replaced with random integers between 150 and 180 as instructed. Therefore, the updated Height values do not represent actual employee heights.
- **Missing College values:** The 84 missing College values were retained because College was not required for the analysis.
- **Correlation:** Correlation indicates association, not causation.
- **Age groups:** The age categories were selected for this analysis. Different age intervals may produce different distributions.

## Project Structure

```text
ABC-Company-Employee-Analysis/
│
├── ABC_Company_Employee_Analysis.ipynb
├── ABC Company Dataset.csv
├── README.md
│
└── images/
    ├── 1a_team_countplot.png
    ├── 1b_team_pie.png
    ├── 2_position_bar.png
    ├── 3_age_group_bar.png
    ├── 4_salary_stacked.png
    └── 5_age_salary_regplot.png
```

## How to Run the Project

1. Download or clone this repository.
2. Install the required Python libraries:

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

3. Keep the CSV dataset in the same folder as the Jupyter Notebook.
4. Open the notebook using Jupyter Notebook.
5. Update the CSV file path if necessary.
6. Select **Kernel → Restart & Run All** to execute the complete analysis and generate the visualisations.

---

**Project:** ABC Company Employee Data Analysis  
**Tools:** Python, Pandas, NumPy, Matplotlib, Seaborn and Jupyter Notebook

**Author:** Neethu Joseph
