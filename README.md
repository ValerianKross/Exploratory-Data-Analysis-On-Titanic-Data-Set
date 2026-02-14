# Titanic Survival Analysis

Exploratory data analysis investigating factors that influenced passenger survival on the Titanic.

## Overview

This project analyzes the Titanic dataset to understand how gender, passenger class, and port of embarkation affected survival rates. I perform data preprocessing, encode categorical variables, calculate survival statistics, and create visualizations to reveal patterns in the data.

## Key Findings

| Factor | Survival Rate | Insight |
|--------|--------------|---------|
| **Female** | 100% | Perfect survival rate |
| **Male** | 0% | No survivors |
| **First Class** | 47% | Highest class survival |
| **Second Class** | 32% | Lowest survival rate |
| **Third Class** | 33% | Comparable to second |
| **Cherbourg** | 33% | Lowest port survival |
| **Queenstown** | 39% | Middle survival |
| **Southampton** | 52% | Highest port survival |

## Dataset

- **Size**: 418 passengers
- **Features**: PassengerId, Survived, Pclass, Name, Sex, Age, SibSp, Parch, Ticket, Fare, Cabin, Embarked
- **Target**: Survived (0 = No, 1 = Yes)

## Encoding Scheme

| Variable | Encoding |
|----------|----------|
| Sex | 0 = Male, 1 = Female |
| Embarked | 0 = Cherbourg (C), 1 = Queenstown (Q), 2 = Southampton (S) |

## Visualizations

- Survival count distribution
- Survival rate by gender
- Survival rate by passenger class
- Correlation heatmap of numeric features

## Technologies

- Python
- pandas
- seaborn
- matplotlib


  ⚠️  IMPORTANT: This dataset exhibits an extreme gender-based survival 
    split (100% female survival, 0% male survival) that does not 
    reflect actual historical Titanic data. In reality, approximately 
    74% of women and 19% of men survived. This pattern suggests the 
    dataset may be:
  
    • Synthetic or artificially generated
  
    • A curated subset with selection bias  
    • Contain predicted labels rather than historical outcomes

    Interpret results accordingly.

## Usage

```python
import pandas as pd

# Load data
df = pd.read_csv('titanic_data.csv')

# Encode categorical variables
df['Sex_encoded'] = df['Sex'].map({'male': 0, 'female': 1})
df['Embarked_encoded'] = df['Embarked'].map({'C': 0, 'Q': 1, 'S': 2})

# Calculate survival rates
print(df.groupby('Sex_encoded')['Survived'].mean())
print(df.groupby('Pclass')['Survived'].mean())

