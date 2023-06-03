# Ex-08-Data-Visualization-

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

![Screenshot (470)](https://github.com/VIJAYKUMAR22007124/Ex-08-Data-Visualization-/assets/119657657/f6f0f436-dbbc-4a53-a21c-b2873e3adc78)


![Screenshot (471)](https://github.com/VIJAYKUMAR22007124/Ex-08-Data-Visualization-/assets/119657657/e5b43b6c-e5ed-4f5d-8c58-9b7dde716af5)


![Screenshot (472)](https://github.com/VIJAYKUMAR22007124/Ex-08-Data-Visualization-/assets/119657657/b8840c4b-b142-4a90-9f9b-ace301e23719)


![Screenshot (473)](https://github.com/VIJAYKUMAR22007124/Ex-08-Data-Visualization-/assets/119657657/1f084e47-a586-41d2-914b-4227175a20ee)


![Screenshot (474)](https://github.com/VIJAYKUMAR22007124/Ex-08-Data-Visualization-/assets/119657657/67ce4c00-57f2-41be-ac09-35bb04e43d43)


![Screenshot (475)](https://github.com/VIJAYKUMAR22007124/Ex-08-Data-Visualization-/assets/119657657/456537c2-5794-4042-884a-567b3d114eaf)


![Screenshot (476)](https://github.com/VIJAYKUMAR22007124/Ex-08-Data-Visualization-/assets/119657657/c8786d01-5ad7-41a8-920f-67bcc20cdc66)


![kk](https://github.com/VIJAYKUMAR22007124/Ex-08-Data-Visualization-/assets/119657657/176bc604-ec8a-4e12-9532-e06e2e90050f)


![Screenshot (477)](https://github.com/VIJAYKUMAR22007124/Ex-08-Data-Visualization-/assets/119657657/658aa042-deae-4d4c-a799-21a27fe0e064)


![Screenshot (478)](https://github.com/VIJAYKUMAR22007124/Ex-08-Data-Visualization-/assets/119657657/bf053212-a20f-45be-9530-2283d071e9d0)


![Screenshot (479)](https://github.com/VIJAYKUMAR22007124/Ex-08-Data-Visualization-/assets/119657657/74e9d902-2353-410c-bc99-02bb57090c00)


![Screenshot (480)](https://github.com/VIJAYKUMAR22007124/Ex-08-Data-Visualization-/assets/119657657/8de33981-4819-4cfc-b389-c36bbf810e45)


![Screenshot (483)](https://github.com/VIJAYKUMAR22007124/Ex-08-Data-Visualization-/assets/119657657/26c5b804-1f34-4cd9-ad01-532193cc55ef)


![Screenshot (484)](https://github.com/VIJAYKUMAR22007124/Ex-08-Data-Visualization-/assets/119657657/7893617d-6f6d-4498-8090-f9d8b9e91488)


![Screenshot (485)](https://github.com/VIJAYKUMAR22007124/Ex-08-Data-Visualization-/assets/119657657/79f9d2c2-9423-4423-80b8-21b8ae29c8d9)


![Screenshot (486)](https://github.com/VIJAYKUMAR22007124/Ex-08-Data-Visualization-/assets/119657657/76ced430-e1d5-4e2a-b0c9-1a6272a67a18)


![Screenshot (487)](https://github.com/VIJAYKUMAR22007124/Ex-08-Data-Visualization-/assets/119657657/7e716fc9-2707-4a65-ab28-e1ec2df2b10f)


# RESULT:

Performed Data Visualization on the given dataset and saveed the data to a file.
