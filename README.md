# FIND-S Algorithm

import pandas as pd

# Training data
data = {
    'Sky': ['Sunny','Sunny','Rainy','Sunny'],
    'AirTemp': ['Warm','Warm','Cold','Warm'],
    'Humidity': ['Normal','High','High','High'],
    'Wind': ['Strong','Strong','Strong','Weak'],
    'Water': ['Warm','Warm','Warm','Warm'],
    'Forecast': ['Same','Same','Change','Same'],
    'PlayTennis': ['Yes','Yes','No','Yes']
}

df = pd.DataFrame(data)

# Initialize hypothesis
hypothesis = ['0'] * (len(df.columns) - 1)

for index, row in df.iterrows():
    if row['PlayTennis'] == 'Yes':
        for i in range(len(hypothesis)):
            if hypothesis[i] == '0':
                hypothesis[i] = row[i]
            elif hypothesis[i] != row[i]:
                hypothesis[i] = '?'

print("Most Specific Hypothesis:")
print(hypothesis)
