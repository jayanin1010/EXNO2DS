# EXNO2DS
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
            
            import pandas as pd
            import seaborn as sns

            df=pd.read_csv("titanic_dataset.csv")
            df

<img width="1326" height="514" alt="image" src="https://github.com/user-attachments/assets/fc49f6c0-41a1-46fa-a72f-03a08f54ed19" />

            df.shape
            df.info()
            df.describe()

<img width="990" height="767" alt="image" src="https://github.com/user-attachments/assets/37ea7aa6-52ca-418f-b55c-e85b0213b39e" />

            df.set_index("PassengerId",inplace=True)
            df

<img width="1336" height="557" alt="image" src="https://github.com/user-attachments/assets/d249c445-a959-4faf-b737-fdd501daf28b" />

            df.isnull()

<img width="1139" height="560" alt="image" src="https://github.com/user-attachments/assets/8c456ede-89a0-4f01-b0b5-272b47445986" />

            print(df.isnull().sum())
            df.nunique()

<img width="372" height="269" alt="image" src="https://github.com/user-attachments/assets/a1d2417c-da85-42b3-ab55-918b1654c16e" />

            #total values
            df['Survived'].value_counts()

<img width="389" height="101" alt="image" src="https://github.com/user-attachments/assets/12f70deb-bfed-4446-836b-fb1b6b8e872d" />

            #unique values in that column
            df.Survived.unique()

<img width="170" height="30" alt="image" src="https://github.com/user-attachments/assets/d4536cc2-c0f7-4f44-9493-55752c749c4d" />


            #univariate analysis
            #grouping based on sex
            sns.countplot(x="Survived",hue='Sex',data=df)

<img width="1350" height="580" alt="image" src="https://github.com/user-attachments/assets/3a1174d7-2e92-4115-81bb-9bebc7933f71" />

            df.rename(columns={'Sex':'Gender'},inplace=True)
            df

<img width="1393" height="539" alt="image" src="https://github.com/user-attachments/assets/03e0ae13-9eb4-4df1-940a-8ba045b53132" />

            sns.countplot(x="Gender",hue='Pclass',data=df)

<img width="1117" height="579" alt="image" src="https://github.com/user-attachments/assets/a970ab65-80ab-4d7e-a5ff-873d6e062c50" />

            sns.catplot(x="Survived",hue="Gender",data=df,kind='violin')
<img width="918" height="651" alt="image" src="https://github.com/user-attachments/assets/6908a211-b965-45f6-aa53-7ba5690b08fc" />


            sns.catplot(x="Survived",hue="Gender",data=df,kind='count')
<img width="934" height="649" alt="image" src="https://github.com/user-attachments/assets/e8b21046-becc-4612-bc66-12356b926137" />

            sns.catplot(x="Survived",col="Gender",data=df,kind='count')
<img width="1320" height="654" alt="image" src="https://github.com/user-attachments/assets/574b8ca7-3071-49eb-8754-7858c1e82220" />


            sns.boxplot(data=df)
<img width="922" height="544" alt="image" src="https://github.com/user-attachments/assets/d14aaf79-8ce2-4d00-9245-3cb2304b4e5c" />

            
            df.boxplot(column='Age',by='Pclass')
<img width="1103" height="611" alt="image" src="https://github.com/user-attachments/assets/14b3f3e2-cfdd-4ac6-861e-a659295f2871" />


            sns.scatterplot(x='Age',y='Fare',data=df)
<img width="1073" height="575" alt="image" src="https://github.com/user-attachments/assets/715341dc-1084-4b94-b101-8a2fd69520ba" />


            sns.jointplot(x='Age',y='Fare',data=df)
<img width="1142" height="786" alt="image" src="https://github.com/user-attachments/assets/7384dffc-9019-49ed-b10b-6f1676b8cc5d" />


            sns.jointplot(x='Age',y='Fare',data=df,kind='kde')
<img width="934" height="771" alt="image" src="https://github.com/user-attachments/assets/446aa994-1801-44db-857e-7e3fe8f90da6" />


            sns.jointplot(x='Age',y='Fare',data=df,kind='hist')
<img width="1038" height="760" alt="image" src="https://github.com/user-attachments/assets/204c6b12-1e3a-4f01-ac1d-a42176961369" />

            #pairwise relationship
            sns.pairplot(data=df)
<img width="1388" height="828" alt="image" src="https://github.com/user-attachments/assets/e7e3a3d0-d7c9-4376-8437-e552a682722d" />


            #multivariate analysis
            cor1=df.select_dtypes(include=['number']).corr()
            sns.heatmap(cor1,annot=True)
<img width="821" height="565" alt="image" src="https://github.com/user-attachments/assets/1d1dd781-9153-48f0-a661-c410659e60d4" />


            group=df.groupby(['Pclass','Survived'])
            pclass_survived=group.size().unstack()
            sns.heatmap(pclass_survived,annot=True,fmt='d')
<img width="891" height="579" alt="image" src="https://github.com/user-attachments/assets/14d0ef89-49e0-44a4-8040-765e8c27fd42" />


# RESULT
        Thus the given titanic dataset is analysed through exploratory data analysis.
