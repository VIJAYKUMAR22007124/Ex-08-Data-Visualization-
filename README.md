# Ex-07-Data-Visualization-

## AIM
To Perform Data Visualization on the given dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.


# CODE
```
import pandas as pd
df = pd.read_csv("/content/Superstore (1).csv",encoding='windows-1252')
df

df.isnull()
df.dropna(how = "all")
df.dropna(how="any")
df.isnull().sum()

SALES VS SEGMENTS:

import matplotlib.pyplot as plt
import seaborn as sns
sns.lineplot(x="Segment",y="Sales",data = df,marker="o",markersize=8,markerfacecolor="blue")
plt.xticks(rotation =90)
plt.show()

CITY VS PROFIT:
tot=df.loc[:,["City","Profit"]]
tot=tot.groupby(by=['City']).sum().sort_values(by=['Profit'])
plt.figure(figsize=(80,20))
sns.barplot(x=tot.index,y='Profit',data=tot)
plt.xticks(rotation=90)


SEGMENT VS PROFIT:
sns.barplot(x="Segment",y="Profit",data=df)
plt.show()

SHIP MODE VS PROFIT:
sns.lineplot(x="Ship Mode",y="Profit",data = df,marker="o",markersize=4,markerfacecolor="blue")
plt.xticks(rotation =90)
plt.show()

sns.barplot(x="Ship Mode",y="Profit",data=df)
plt.show()

SALES VS PRODUCT ("REGION")
sns.barplot(x="Category",y="Sales",data=df,hue="Region")
plt.show()

SALES VS PROFIT:
sns.lineplot(x="Sales",y="Profit",data = df,marker="o",markersize=4,markerfacecolor="blue")
plt.xticks(rotation =90)
plt.show()

sns.barplot(x="Sales",y="Profit",data=df)
plt.show()

SALES VS PROFIT:
1) STATE
grouped_data = df.groupby('State')[['Sales', 'Profit']].mean()
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('State')
ax.set_ylabel('Value')
ax.legend()
plt.show()

2)REGION
df.groupby(['Region']).sum().plot(kind='pie', y='Sales',figsize=(6,9),pctdistance=1.7,labeldistance=1.2)
df["Sales"].corr(df["Profit"])
df_corr = df.copy()
df_corr = df_corr[["Sales","Profit"]]
df_corr.corr()

3)SEGMENT,SHIP MODE
grouped_data = df.groupby(['Segment', 'Ship Mode'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index='Segment', columns='Ship Mode', values=['Sales', 'Profit'])

fig, ax = plt.subplots()
pivot_data.plot(kind='bar', ax=ax)
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
plt.legend(title='Ship Mode')
plt.show()

4)SEGMENT,SHIP MODE,REGION:
grouped_data = df.groupby(['Segment', 'Ship Mode','Region'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index=['Segment', 'Ship Mode'], columns='Region', values=['Sales', 'Profit'])
sns.set_style("whitegrid")
sns.set_palette("Set1")
pivot_data.plot(kind='bar', stacked=True, figsize=(10, 15))
plt.legend(title='Region')
plt.show()

```

# OUPUT
