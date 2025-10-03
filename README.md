# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```py
import pandas as pd
df=pd.read_csv("Data_set.csv")
df
```
<img width="820" height="698" alt="image" src="https://github.com/user-attachments/assets/969079fb-7fcb-4145-9496-58f51e599767" />

```py
df.head()
```
<img width="827" height="201" alt="image" src="https://github.com/user-attachments/assets/3a36b996-875a-475f-b585-658fc23d6858" />

```py
df.tail()
```
<img width="813" height="193" alt="image" src="https://github.com/user-attachments/assets/f4c61c1b-a997-4e94-ac6a-336dcf86a375" />

```py
df.isnull()
```
<img width="662" height="691" alt="image" src="https://github.com/user-attachments/assets/458d424f-079e-4ac3-aadf-5e414816c365" />

```py
df.isnull().sum()
```
<img width="179" height="451" alt="image" src="https://github.com/user-attachments/assets/760600ce-86e8-4b05-8362-400d582c540d" />

```py
df.isnull().any()
```
<img width="259" height="451" alt="image" src="https://github.com/user-attachments/assets/86894533-6bb8-415c-b81e-a7f465a4937c" />

```py
df.dropna(axis=0)
```
<img width="828" height="447" alt="image" src="https://github.com/user-attachments/assets/bbddcfad-afb1-4de1-82a7-457d57d925a5" />

```py
df.dropna(axis=1)
```
<img width="248" height="709" alt="image" src="https://github.com/user-attachments/assets/c2267afc-f5f3-4558-ac79-0d5a94629e16" />

```py
df.fillna("empty")
```
<img width="858" height="696" alt="image" src="https://github.com/user-attachments/assets/7abfaae5-3566-4e24-a970-355f058d33ab" />

```py
df.fillna(method='ffill')
```
<img width="820" height="695" alt="image" src="https://github.com/user-attachments/assets/b8b48513-fedb-4ac8-b89a-351774162e73" />

```py
df.fillna(method='bfill')
```
<img width="821" height="688" alt="image" src="https://github.com/user-attachments/assets/ddb20000-cd2a-4f0e-8243-433ad5422f12" />

```py
df.fillna({'NAME':'SRI','GENDER':'MALE','ADDRESS':'CHITHUR','M1':90,'M2':90,'M3':89,'M4':87})
```
<img width="809" height="703" alt="image" src="https://github.com/user-attachments/assets/7e40dccf-d9f4-4719-a739-d362761f2ced" />

```py
ir=pd.read_csv("iris.csv")
ir
```
<img width="528" height="386" alt="image" src="https://github.com/user-attachments/assets/25f51946-fcaa-49d1-819d-5368174cc360" />

```py
ir.describe()
```
<img width="473" height="291" alt="image" src="https://github.com/user-attachments/assets/13bdf354-5e41-4f0c-8b5d-4169e707467b" />

```py
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
<img width="553" height="455" alt="image" src="https://github.com/user-attachments/assets/ab82f349-8b58-4c77-b43d-6756b6419507" />

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
<img width="772" height="34" alt="image" src="https://github.com/user-attachments/assets/de0b02df-0536-45fd-9ad8-aa98337c73a0" />

```py
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```
<img width="184" height="204" alt="image" src="https://github.com/user-attachments/assets/70e60235-ad24-4cb3-9c0e-4612c66791ec" />

```py
delid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
delid
```
<img width="534" height="404" alt="image" src="https://github.com/user-attachments/assets/b83bfaa6-66a5-4518-83d9-118be88d015e" />

```py
sns.boxplot(x='sepal_width',data=delid)
```
<img width="545" height="447" alt="image" src="https://github.com/user-attachments/assets/9a6d7a59-1197-43cd-9444-9e1f48483153" />

```py
z=np.abs(stats.zscore(ir['sepal_width']))
z
```
<img width="569" height="530" alt="image" src="https://github.com/user-attachments/assets/f525fe24-5c7c-47e1-a62f-92338cb81cce" />

```py
ir1=ir[z<3]
ir1
```
<img width="534" height="406" alt="image" src="https://github.com/user-attachments/assets/bf7ba979-43cb-4587-93be-1347f5a6f7de" /> <<include your coding and its corressponding output screen shots here>>
# Result
          <<include your Result here>>
