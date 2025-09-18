# 🚢 Titanic Survival Analysis  

## 📌 Project Overview  
This project is an analysis of the **Titanic dataset** from Kaggle.  
The main objective is to practice **data cleaning**, **exploratory data analysis (EDA)**, and **data visualization** to uncover patterns that influenced passenger survival during the Titanic disaster.  

---

## 🔹 Project Requirements  

### 1. Data Cleaning  
- Fill missing `Age` values with mean.  
- Drop irrelevant columns (`Cabin`, `Ticket`, `Name`, `PassengerId`).  
- Create a new feature `Family_Size = SibSp + Parch`.  

### 2. Analysis Questions  
- Survival rate by **Age Group**.  
- Survival rate by **Embarkation Port**.  
- Survival rate by **Family Size**.  

### 3. Visualizations  
- Age distribution (**histogram**).  
- Correlation (**heatmap**).  
- Survival by family size (**bar plot**).  

---

## 📊 Sample Code  

```python
# Import libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset
df = pd.read_csv('titanic.csv')

# Clean dataset
df['Age'].fillna(df['Age'].mean(), inplace=True)
df.drop(columns=['Cabin','Ticket','Name','PassengerId'], inplace=True)

# Create Family Size feature
df['Family_Size'] = df['SibSp'] + df['Parch']

# Example: Survival rate by Age Group
bins = [0, 12, 18, 35, 60, 100]
labels = ['Child', 'Teen', 'Adult', 'Middle Age', 'Senior']
df['Age_Group'] = pd.cut(df['Age'], bins=bins, labels=labels)

print(df.groupby('Age_Group')['Survived'].mean())

🔍 Insights & Conclusion

Children had higher survival rates compared to adults and seniors.

Passengers from Cherbourg had better survival chances than those from Southampton or Queenstown.

Small families had higher survival rates, while larger families struggled.

Passenger class strongly influenced survival.
