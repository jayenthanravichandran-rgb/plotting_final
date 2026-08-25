# # Exp 6 Analysis and Visualization of COVID-19 Dataset using Python

**Date:**

## AIM:

To analyse a large real-world COVID-19 dataset using Python and visualize key trends and relationships using multiple types of graphs for meaningful insights.

## DESIGN STEPS:

### Step 1:

Clone the repository from GitHub.

### Step 2:

Create a Python project in the preferred IDE (VS Code/PyCharm/Jupyter Notebook).

### Step 3:

Create the Python program for analysing and visualizing the COVID-19 dataset using **Pandas** and **Matplotlib** libraries.

### Step 4:

Load the **`covid_cases.csv`** dataset using Pandas and explore the dataset by displaying its shape and column names.

### Step 5:

Check and handle missing values in the dataset, if any.

### Step 6:

Perform basic data exploration by finding the total number of records and generating the statistical summary using the `describe()` function.

### Step 7:

Use Matplotlib to create different visualizations:

* **Line Graph:** Trend of confirmed cases over time globally.
* **Bar Chart:** Top 10 countries by total confirmed cases.
* **Pie Chart:** Case distribution of the top 5 affected countries.
* **Scatter Plot:** Relationship between confirmed cases and deaths.
* **Histogram:** Distribution of active cases.

### Step 8:

Add appropriate titles, axis labels, legends, and other necessary labels to the graphs.

### Step 9:

Execute the program and analyze the generated visualizations to identify meaningful trends and relationships in the COVID-19 dataset.

## PROGRAM:

import pandas as pd
import matplotlib.pyplot as plt

# Load dataset
data = pd.read_csv("covid_case.csv")

# Display basic information
print("First 5 rows:")
print(data.head())

print("\nDataset Shape:")
print(data.shape)

print("\nColumn Names:")
print(data.columns)

# Check missing values
print("\nMissing Values:")
print(data.isnull().sum())

# Remove missing values
data = data.dropna()

# Convert Date column to datetime
data['Date'] = pd.to_datetime(data['Date'])

# Total number of records
print("\nTotal Records:", len(data))

# Statistical summary
print("\nStatistical Summary:")
print(data.describe())

# Line Graph: Global confirmed cases over time
global_cases = data.groupby('Date')['Confirmed'].sum()

plt.figure()
plt.plot(global_cases.index, global_cases.values)
plt.title("Global Confirmed COVID-19 Cases Over Time")
plt.xlabel("Date")
plt.ylabel("Confirmed Cases")
plt.show()

# Bar Chart: Top 10 countries by confirmed cases
top10 = data.groupby('Country')['Confirmed'].sum().sort_values(ascending=False).head(10)

plt.figure()
top10.plot(kind='bar')
plt.title("Top 10 Countries by Confirmed Cases")
plt.xlabel("Country")
plt.ylabel("Confirmed Cases")
plt.show()

# Pie Chart: Top 5 affected countries
top5 = data.groupby('Country')['Confirmed'].sum().sort_values(ascending=False).head(5)

plt.figure()
plt.pie(top5, labels=top5.index, autopct='%1.1f%%')
plt.title("Top 5 Countries Case Distribution")
plt.show()

# Scatter Plot: Confirmed vs Deaths
plt.figure()
plt.scatter(data['Confirmed'], data['Deaths'])
plt.title("Confirmed Cases vs Deaths")
plt.xlabel("Confirmed Cases")
plt.ylabel("Deaths")
plt.show()

# Histogram: Distribution of active cases
plt.figure()
plt.hist(data['Active'], bins=20)
plt.title("Distribution of Active Cases")
plt.xlabel("Active Cases")
plt.ylabel("Frequency")
plt.show()


## OUTPUT:

<img width="1901" height="977" alt="Screenshot 2026-08-25 093330" src="https://github.com/user-attachments/assets/4c04b609-d2f8-4d1c-8ea6-3943ca8c811d" />
<img width="932" height="426" alt="Screenshot 2026-08-25 093402" src="https://github.com/user-attachments/assets/3cb2371b-48bb-4d7c-8905-1ab07d0ebde5" />
<img width="696" height="321" alt="Screenshot 2026-08-25 093430" src="https://github.com/user-attachments/assets/0714d88f-8f00-4333-9273-30e61921427b" />
<img width="851" height="388" alt="Screenshot 2026-08-25 093458" src="https://github.com/user-attachments/assets/ee732d8f-b7a9-4630-a577-743531b24dd3" />
<img width="912" height="390" alt="Screenshot 2026-08-25 093521" src="https://github.com/user-attachments/assets/dd0dab97-6837-4735-9c34-e10ec72ce0b3" />



## RESULT:

The COVID-19 dataset was successfully analysed using Python. The dataset was explored using Pandas, and meaningful trends and relationships were visualized using different types of graphs such as line graph, bar chart, pie chart, scatter plot, and histogram using Matplotlib.
