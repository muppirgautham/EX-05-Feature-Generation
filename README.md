# EX-05-Feature-Generation


## AIM
To read the given data and perform Feature Generation process and save the data to a file. 

# Explanation
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.
 

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature Generation techniques to all the feature of the data set
### STEP 4
Save the data to the file


# CODE :
```
Program Developed: GAUTHAM M
Register number:212221230027
```
# Data.csv :
```
import pandas as pd
df=pd.read_csv("data.csv")
df

#feature generation
import category_encoders as ce
be=ce.BinaryEncoder()
ndf=be.fit_transform(df["bin_1"])
df["bin_1"] = be.fit_transform(df["bin_1"])
ndf

ndf2=be.fit_transform(df["bin_2"])
df["bin_2"] = be.fit_transform(df["bin_2"])
ndf2

df1=df.copy()
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder,OneHotEncoder
import category_encoders as ce
be=ce.BinaryEncoder()
ohe=OneHotEncoder(sparse=False)
le=LabelEncoder()
oe=OrdinalEncoder()


df1["City"] = ohe.fit_transform(df1[["City"]])

temp=['Cold','Warm','Hot','Very Hot']
oe1=OrdinalEncoder(categories=[temp])
df1['Ord_1'] = oe1.fit_transform(df1[["Ord_1"]])

edu=['High School','Diploma','Bachelors','Masters','PhD']
oe2=OrdinalEncoder(categories=[edu])
df1['Ord_2']= oe2.fit_transform(df1[["Ord_2"]])
df1

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df2=pd.DataFrame(sc.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df2

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df3=pd.DataFrame(sc1.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df3

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df4=pd.DataFrame(sc2.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df4

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df5=pd.DataFrame(sc3.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df5
```
# Encoding.csv :
```
import pandas as pd
df=pd.read_csv("Encoding Data.csv")
df

#feature generation
import category_encoders as ce
be=ce.BinaryEncoder()
ndf=be.fit_transform(df["bin_1"])
df["bin_1"] = be.fit_transform(df["bin_1"])
ndf

ndf2=be.fit_transform(df["bin_2"])
df["bin_2"] = be.fit_transform(df["bin_2"])
ndf2

df1=df.copy()
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
le=LabelEncoder()
oe=OrdinalEncoder()

df1["nom_0"] = oe.fit_transform(df1[["nom_0"]])
temp=['Cold','Warm','Hot']
oe2=OrdinalEncoder(categories=[temp])
df1['ord_2'] = oe2.fit_transform(df1[['ord_2']])

df1

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df0=pd.DataFrame(sc.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df0

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df2=pd.DataFrame(sc1.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df2

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df3=pd.DataFrame(sc2.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df3

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df4=pd.DataFrame(sc3.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df4
```
# Titanic.csv :
```
import pandas as pd
df=pd.read_csv("titanic_dataset.csv")
df

#removing unwanted data
df.drop("Name",axis=1,inplace=True)
df.drop("Ticket",axis=1,inplace=True)
df.drop("Cabin",axis=1,inplace=True)

#data cleaning
df.isnull().sum()

df["Age"]=df["Age"].fillna(df["Age"].median())
df["Embarked"]=df["Embarked"].fillna(df["Embarked"].mode()[0])

df.isnull().sum()

df

#feature encoding
from category_encoders import BinaryEncoder
be=BinaryEncoder()
df["Sex"]=be.fit_transform(df[["Sex"]])
ndf=be.fit_transform(df["Sex"])
ndf

df1=df.copy()
from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
embark=['S','C','Q']
e1=OrdinalEncoder(categories=[embark])
df1['Embarked'] = e1.fit_transform(df[['Embarked']])
df1

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df2=pd.DataFrame(sc.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df2

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df3=pd.DataFrame(sc1.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df3

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df4=pd.DataFrame(sc2.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df4

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df5=pd.DataFrame(sc3.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df5
```

# OUPUT :
# Data.csv : 
![o1](https://user-images.githubusercontent.com/94810884/167258082-bdd4d6d4-d2fd-44db-8cbb-3dc21273d33e.png)
![o2](https://user-images.githubusercontent.com/94810884/167258087-da021360-e029-42d3-8d4e-1c3487e9156a.png)
![o3](https://user-images.githubusercontent.com/94810884/167258098-f85a0c7a-564a-42b4-9e74-4073a08c03c4.png)
![04](https://user-images.githubusercontent.com/94810884/167258125-6864eb04-67bc-460d-bea1-681ec2dcb6b5.png)
![o5](https://user-images.githubusercontent.com/94810884/167258112-a71d7ba3-67fe-414c-8d49-f46504ff2216.png)
![o6](https://user-images.githubusercontent.com/94810884/167258117-aad2e88c-6775-4107-bb6c-11799b2fe357.png)
![o7](https://user-images.githubusercontent.com/94810884/167258135-d337d134-9e64-4380-97c4-d18c4af3b726.png)
![o8](https://user-images.githubusercontent.com/94810884/167258145-3ca961be-3006-4f0b-ba02-62994097b81a.png)
# Encoding.csv :
![o9](https://user-images.githubusercontent.com/94810884/167258150-abf72e5d-8409-4cc0-86e1-635796a1e603.png)
![o10](https://user-images.githubusercontent.com/94810884/167258168-53b0373c-4cd5-4495-a0f9-e6e3decdbad8.png)
![o11](https://user-images.githubusercontent.com/94810884/167258181-62448947-a703-4668-92e0-47dafa4d9294.png)
![o12](https://user-images.githubusercontent.com/94810884/167258187-40f2ef68-79d1-43f2-9840-e5c95ace585f.png)
![o13](https://user-images.githubusercontent.com/94810884/167258195-7a4c9937-ef15-411f-a9dc-d8754c17c6c4.png)
![o14](https://user-images.githubusercontent.com/94810884/167258204-9c584a31-5c27-4177-b8a3-0cbceba190f7.png)
![o15](https://user-images.githubusercontent.com/94810884/167258210-26d26831-97e1-4d76-bebe-4fd11b716be5.png)
![o16](https://user-images.githubusercontent.com/94810884/167258218-d4868fe3-6149-4eca-87b5-f0a4c286ed60.png)
![o17](https://user-images.githubusercontent.com/94810884/167258226-869ee42c-312e-4275-8a0d-de0cf7df87d6.png)
![o18](https://user-images.githubusercontent.com/94810884/167258235-37ad9a6f-374d-4116-8a93-5406a781bc19.png)
![o19](https://user-images.githubusercontent.com/94810884/167258242-9af89992-959e-47de-805e-16d3b7f2b065.png)
![o20](https://user-images.githubusercontent.com/94810884/167258249-646eab95-3589-4e09-bcfd-8aa74c851097.png)
![o21](https://user-images.githubusercontent.com/94810884/167258256-2dfa007b-19ef-49ef-8eda-767ba939c8f8.png)
# Titanic.csv :
![o22](https://user-images.githubusercontent.com/94810884/167258260-786c2a18-ca7e-4859-981e-e973b5dd1d44.png)
![o23](https://user-images.githubusercontent.com/94810884/167258264-f9bfbbf7-1236-418e-b1e5-f130d57ef866.png)
![o24](https://user-images.githubusercontent.com/94810884/167258274-2478acf8-106d-4dfa-af7d-c8ea729c5e68.png)
![o25](https://user-images.githubusercontent.com/94810884/167258276-e2009cd6-696d-45c7-9c12-3d8d489b8ac4.png)
![o26](https://user-images.githubusercontent.com/94810884/167258283-5e84dffb-0a0a-402d-ac37-e1e9b201a47f.png)
![o27](https://user-images.githubusercontent.com/94810884/167258287-0d9bc1dd-92ab-4974-b4ac-8112be4bd101.png)

# RESULT:
Feature Generation process and Feature Scaling process is applied to the given data frames sucessfully.




