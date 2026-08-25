# # Exp 6 Analysis and Visualization of COVID-19 Dataset using Python

**Date:25.08.2026**

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

*(Paste the Python code for COVID-19 Dataset Analysis and Visualization here.)*
```
from google.colab import files
uploaded = files.upload()
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
```
## OUTPUT:

*(Paste the execution output showing the dataset information, statistical summary, and generated Line Graph, Bar Chart, Pie Chart, Scatter Plot, and Histogram.)*
<img width="937" height="562" alt="Screenshot 2026-08-25 104924" src="https://github.com/user-attachments/assets/0b6d7e27-fba9-4720-92ba-49c89c62178d" />

<img width="929" height="523" alt="Screenshot 2026-08-25 104948" src="https://github.com/user-attachments/assets/53d72e10-561a-44c9-b576-4b19710afc33" />
<img width="917" height="427" alt="Screenshot 2026-08-25 105008" src="https://github.com/user-attachments/assets/35ef9df7-14bb-4dca-a276-90829458a516" />
<img width="1051" height="328" alt="Screenshot 2026-08-25 105024" src="https://github.com/user-attachments/assets/1bcf48a9-6382-4072-b0a1-a5c315bcfd1d" />
<img width="651" height="370" alt="Screenshot 2026-08-25 105037" src="https://github.com/user-attachments/assets/0b115895-b612-432d-a170-3055f05a3f11" />
<img width="917" height="376" alt="Screenshot 2026-08-25 105051" src="https://github.com/user-attachments/assets/0c08ff0e-a665-4244-a16a-bd376d3c3bd3" />

## RESULT:

The COVID-19 dataset was successfully analysed using Python. The dataset was explored using Pandas, and meaningful trends and relationships were visualized using different types of graphs such as line graph, bar chart, pie chart, scatter plot, and histogram using Matplotlib.
