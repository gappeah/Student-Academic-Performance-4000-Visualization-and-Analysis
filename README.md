
# Student Academic Performance 4000: Visualisation and Analysis

This project analyses academic performance using a simulated dataset of 4,000 students, exploring how factors like gender, study habits, tutoring, region, attendance, and parental education relate to exam scores. The analysis is performed in a Jupyter Notebook with visualisations and code for reproducibility.



## Dataset: SAP-4000.csv

### About Dataset
The SAP-4000 Dataset: Investigating Determinants of Academic Success in Spain’s Título de Bachiller encompasses 4,000 anonymised student records, meticulously compiled to analyse the multifaceted factors influencing academic performance in Spain’s upper secondary education system, culminating in the Título de Bachiller. This qualification is pivotal, as it not only signifies the completion of secondary education but also serves as a prerequisite for university admission via the Evaluación de Bachillerato para el Acceso a la Universidad (EBAU).

Recognising the complexity of academic achievement, the dataset integrates a diverse array of variables, including demographic information, study habits, educational support mechanisms, and final examination outcomes. This comprehensive approach facilitates a nuanced exploration of how these factors interact and contribute to student success.

**Columns:**
- `Gender`: Student's gender (Male, Female)
- `HoursStudied/Week`: Average hours studied per week (float)
- `Tutoring`: Whether the student receives tutoring (Yes/No)
- `Region`: Student's region (Urban/Rural)
- `Attendance(%)`: Attendance percentage (float)
- `Parent Education`: Highest parental education (None, Primary, Secondary, Tertiary)
- `Exam_Score`: Final exam score (0-100)

**Sample (first rows):**

| Gender | HoursStudied/Week | Tutoring | Region | Attendance(%) | Parent Education | Exam_Score |
|--------|-------------------|----------|--------|---------------|------------------|------------|
| Male   | 5.5               | No       | Urban  | 72.7          | Tertiary         | 43.5       |
| Female | 6.8               | No       | Urban  | 62.0          | Primary          | 51.7       |
| Female | 9.7               | No       | Rural  | 95.0          | Secondary        | 70.1       |

## Data Description

- **No missing data:** All columns are fully populated.
- **Gender balance:** ~51% Female, ~49% Male.
- **Tutoring:** 1,233 Yes; 2,767 No.
- **Region:** 2,423 Urban; 1,577 Rural.
- **Parent Education:** Ranges from None to Tertiary, with the majority having Secondary education.

## Usage

This repository contains:
- [`SAP-4000.csv`](SAP-4000.csv): The dataset.
- [`Student Academic Performance 4000 Visualization and Analysis.ipynb`](Student%20Academic%20Performance%204000%20Visualization%20and%20Analysis.ipynb): Jupyter Notebook for data exploration and visualization.

**Example: Loading the dataset**

```python
import pandas as pd
df = pd.read_csv("SAP-4000.csv")
display(df.head())
```

**Checking for NAs**

```python
df.isna().sum()
```

**Calculating mean study hours**

```python
average_time_studying = df["HoursStudied/Week"].mean()
print(average_time_studying)
```

## Results & Visualizations

### Statistical Highlights

- **Mean study hours per week:** ~9.86
- **Median study hours per week:** 9.9
- **Exam scores:** Range from ~16.6 (min) to 100 (max), mean ~71

### Visualizations

#### 1. Gender Distribution

```python
import matplotlib.pyplot as plt
df_gender = df['Gender'].value_counts()
plt.bar(df_gender.index, df_gender.values)
plt.xlabel('Gender')
plt.ylabel('Count')
plt.title('Gender Distribution')
plt.show()
```
*Bar plot showing nearly equal numbers of male and female students.*

#### 2. Study Time by Parent Education

```python
average_time_studying = df.groupby("Parent Education")["HoursStudied/Week"].mean()
plt.bar(average_time_studying.index, average_time_studying.values)
plt.xlabel("Parent Education")
plt.ylabel("Average Hours Studied/Week")
plt.title("Average Study Time by Parent Education")
plt.show()
```

#### 3. Attendance Distribution by Gender

```python
mean_attendance_by_gender = df.groupby('Gender')['Attendance(%)'].mean()
plt.bar(mean_attendance_by_gender.index, mean_attendance_by_gender.values)
plt.xlabel('Gender')
plt.ylabel('Mean Attendance (%)')
plt.title('Attendance by Gender')
plt.show()
```

#### 4. Pairplot Visualization

```python
import seaborn as sns
sns.pairplot(df.head(100), hue="Gender", corner=True)
plt.show()
```
*Pairplot visualising relationships between numerical variables for the first 100 students, colored by Gender.*

---

## Reproducibility

To run the analysis, open the notebook in Jupyter, ensure you have pandas, numpy, matplotlib, and seaborn installed, and run each cell.

---

## References

- [Kaggle Dataset: Student Academic Performance Simulation 4000](https://www.kaggle.com/datasets/firedmosquito831/student-academic-performance-simulation-4000?resource=download)

---




