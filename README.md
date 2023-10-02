# Ex-04-Multivariate-Analysis

## AIM:
To perform Multivariate EDA on the given data set.

## EXPLANATION:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

## ALGORITHM:
Step1:Import the built libraries required to perform EDA and outlier removal.

Step2:Read the given csv file.

Step3:Convert the file into a dataframe and get information of the data.

Step4:Return the objects containing counts of unique values using (value_counts()).

Step5:Plot the counts in the form of Histogram or Bar Graph.

Step6:Use seaborn the bar graph comparison of data can be viewed.

Step7:Find the pairwise correlation of all columns in the dataframe.corr()

Step8:Save the final data set into the file.

## PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

dt = pd.read_csv('/content/titanic_dataset.csv')

dt

dt.info()

dt.set_index("PassengerId",inplace=True)

dt.shape

dt.describe()

dt.nunique()

dt["Survived"].value_counts()

per = (dt["Survived"].value_counts()/dt.shape[0]*100).round(2)

per

sns.countplot(data=dt,x="Survived")

dt

dt.Pclass.unique()

dt.rename(columns = {'Sex':'Gender'}, inplace = True)
dt

sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5, aspect=.7)

sns.catplot(x='Survived',hue = "Gender",data = dt,kind = "count")

fig, ax1 = plt.subplots(figsize=(8,5))
graph = sns.countplot(ax=ax1,data=dt,x="Survived",hue="Pclass",palette="rainbow")
graph.set_xticklabels(graph.get_xticklabels())
for p in graph.patches:
  height = p.get_height()
  graph.text(p.get_x()+p.get_width()/2, height + 20.8,height,ha="left")

dt.boxplot(column="Age",by="Survived")

sns.scatterplot(x = dt["Age"],y = dt["Fare"])

fig, ax1 = plt.subplots(figsize = (8,5))
pt = sns.boxplot(ax = ax1,x = 'Pclass',y = 'Age', hue='Gender',data=dt)

sns.catplot(data=dt,col="Survived",x="Gender",hue ="Pclass",kind = "count")

g = sns.catplot(data=dt,col="Survived",x="Gender",hue ="Pclass",kind = "count",legend=True)
g.fig.set_size_inches(8,5)
g.fig.subplots_adjust(top=0.81,right=0.86)
ax = g.facet_axis(0,0)
for p in ax.patches:
  ax.text(p.get_x()- 0.01,p.get_height() * 1.02,'{0:.1f}'.format(p.get_height()),color='red',rotation='horizontal',size='small')

## Co-relation
corr = dt.corr()
sns.heatmap(corr,annot=True)

sns.pairplot(dt)
```
## OUTPUT:

![image](https://github.com/Anuayshh/Expt4-ds/assets/127651217/f753b5d2-7ebe-40ca-9973-5686a3c1d976)


![image](https://github.com/Anuayshh/Expt4-ds/assets/127651217/5322cdaa-fd49-47fe-8e4c-cd8203e40642)

![image](https://github.com/Anuayshh/Expt4-ds/assets/127651217/8fe28664-675e-43c9-863f-865893cad188)

![image](https://github.com/Anuayshh/Expt4-ds/assets/127651217/1510b037-cccd-47de-b7d3-e7800d6e1743)

![image](https://github.com/Anuayshh/Expt4-ds/assets/127651217/2723634c-c36b-4731-9eaf-48a7c87760bc)


![image](https://github.com/Anuayshh/Expt4-ds/assets/127651217/fab7bd4d-fd46-482a-be97-6a75ae9bfc5e)


![image](https://github.com/Anuayshh/Expt4-ds/assets/127651217/a6ba7ffb-4c11-4bd9-bfbc-f62ccae57fc7)

![image](https://github.com/Anuayshh/Expt4-ds/assets/127651217/358137a7-464f-4b46-ad0d-d8d8435b398b)


![image](https://github.com/Anuayshh/Expt4-ds/assets/127651217/c33ef0b9-45c8-45eb-82a1-6a1956517d9d)

![image](https://github.com/Anuayshh/Expt4-ds/assets/127651217/893068ff-3708-4c8e-84cb-fd8323b2d536)


![image](https://github.com/Anuayshh/Expt4-ds/assets/127651217/5059e69d-a224-4195-b586-1a6c00517ed7)

![image](https://github.com/Anuayshh/Expt4-ds/assets/127651217/1092f5bf-f6b5-45f0-bbdd-1b7811f0e9b6)



![image](https://github.com/Anuayshh/Expt4-ds/assets/127651217/12b7e3dd-c675-4fbd-b07e-41785b61cf15)

![image](https://github.com/Anuayshh/Expt4-ds/assets/127651217/f0f9759e-7188-4462-8fbb-db2d309ec59e)

![image](https://github.com/Anuayshh/Expt4-ds/assets/127651217/6fb7594b-6971-4e96-9378-0b3e039c68fa)

![image](https://github.com/Anuayshh/Expt4-ds/assets/127651217/91cea782-656e-4a77-949b-838042584956)

![image](https://github.com/Anuayshh/Expt4-ds/assets/127651217/411dba76-6bd2-4c15-8251-672dbfe98160)

![image](https://github.com/Anuayshh/Expt4-ds/assets/127651217/2d42c310-b5ee-4e0d-8df6-fe1acea5fb50)

![image](https://github.com/Anuayshh/Expt4-ds/assets/127651217/8aa39901-e944-4bf2-94ed-ec0ac836a7c0)

![image](https://github.com/Anuayshh/Expt4-ds/assets/127651217/e4567297-fe68-488a-98d2-d8c988ed5828)

![image](https://github.com/Anuayshh/Expt4-ds/assets/127651217/39dc9801-b6f4-423c-ae55-265cf07909c5)

## RESULT:
Thus the program to perform EDA on the given data set is successfully executed.
