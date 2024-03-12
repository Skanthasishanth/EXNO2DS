# Exno:2
# AIM:

To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:

The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:

STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
dt=pd.read_csv("titanic.csv")
dt
```

![exp2_ds_1](https://github.com/Skanthasishanth/EXNO2DS/assets/118298456/4f763d41-63df-4295-b2e3-52786bfd8283)

```py
dt.info()
```

![exp2_ds_2](https://github.com/Skanthasishanth/EXNO2DS/assets/118298456/d90e4ee1-89a6-4752-ad63-d9ef49590781)

```py
dt.shape
```

![exp2_ds_3](https://github.com/Skanthasishanth/EXNO2DS/assets/118298456/fb66ad37-024b-4586-a20b-b2c38115207a)

```py
dt.set_index('PassengerId',inplace=True)
dt.describe()
```


![exp2_ds_4](https://github.com/Skanthasishanth/EXNO2DS/assets/118298456/40e7e064-ea2a-406e-96ae-407b8e00d068)


### CATEGORICAL DATA ANALYSIS

```py
dt.nunique()
```

![exp2_ds_5](https://github.com/Skanthasishanth/EXNO2DS/assets/118298456/5aea21a8-5e6f-4e16-85de-a9284b4d5a27)

```py
dt["Survived"].value_counts()
```

![exp2_ds_6](https://github.com/Skanthasishanth/EXNO2DS/assets/118298456/9762540a-ac0d-4444-85a0-8eaba2511bce)

```py
per=(dt["Survived"].value_counts()/dt.shape[0]*100).round(2)
per
```

![exp2_ds_7](https://github.com/Skanthasishanth/EXNO2DS/assets/118298456/c94aa0e3-0750-4331-8743-d82f1ce41dcf)

### UNIVARIATE ANALYSIS

```py
sns.countplot(data=dt,x="Survived")
```

![exp2_ds_8](https://github.com/Skanthasishanth/EXNO2DS/assets/118298456/64b03f2f-ceda-4962-8c9e-f815f28db21c)

```py
dt.Pclass.unique()
```

![exp2_ds_9](https://github.com/Skanthasishanth/EXNO2DS/assets/118298456/a330df81-f526-409f-bd75-d54e683f6a91)

```py
dt.rename(columns={'Sex':'Gender'},inplace=True)
dt
```

![exp2_ds_10](https://github.com/Skanthasishanth/EXNO2DS/assets/118298456/03f8c51f-fd68-450b-a205-e1b6689cdc2b)


### BIVARIATE ANALYSIS

```py
sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5,aspect=.7)
```

![exp2_ds_11](https://github.com/Skanthasishanth/EXNO2DS/assets/118298456/c63a1dab-bcd5-4803-aa70-35d947df0563)

```py
sns.catplot(x='Survived',hue="Gender",data=dt,kind="count")
```

![exp2_ds_12](https://github.com/Skanthasishanth/EXNO2DS/assets/118298456/e25526e4-9c21-445a-9542-8bee39be3a5a)

```py
dt.boxplot(column="Age",by="Survived")
```

![exp2_ds_13](https://github.com/Skanthasishanth/EXNO2DS/assets/118298456/4cdd1acc-abdd-48b2-8ea5-291a4aa25ffb)

```py
sns.scatterplot(x=dt["Age"],y=dt["Fare"])
```

![exp2_ds_14](https://github.com/Skanthasishanth/EXNO2DS/assets/118298456/ecb3219e-9166-41f8-8036-2ac9211896c4)

```py
sns.jointplot(x=dt["Age"],y=dt["Fare"],data=dt)
```

![exp2_ds_15](https://github.com/Skanthasishanth/EXNO2DS/assets/118298456/a21e58d6-8cde-491d-a6c8-c55a750a4b84)

### MULTIVARIATE ANALYSIS

```py
fig,ax1=plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=dt)
```

![exp2_ds_16](https://github.com/Skanthasishanth/EXNO2DS/assets/118298456/045dba05-37ab-4c5a-a9da-144e4ca59bc6)

```py
sns.catplot(data=dt,col="Survived",x="Gender",hue="Pclass",kind="count")
```

![exp2_ds_17](https://github.com/Skanthasishanth/EXNO2DS/assets/118298456/8f5ace67-327f-43dc-9060-de825129c0d4)

```py
corr=dt.corr()
sns.heatmap(corr,annot=True)
```

![exp2_ds_18](https://github.com/Skanthasishanth/EXNO2DS/assets/118298456/65cd8c60-8512-4883-9cef-d988a517a3e5)

```py
sns.pairplot(dt)
```

![exp2_ds_19](https://github.com/Skanthasishanth/EXNO2DS/assets/118298456/4407fde3-76b5-416e-bbf6-442e6c602124)

![exp2_ds_20](https://github.com/Skanthasishanth/EXNO2DS/assets/118298456/ed73e471-ba70-4d80-b465-5b0a281ef9ef)


# RESULT
Thus, Data Analyzing of the given dataset was executed successfully.
