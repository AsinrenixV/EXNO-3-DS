## EXNO-3-DS
## REG NO : 212224040036
## NAME : ASIN RENIX V

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
```
 import pandas as pd
 df=pd.read_csv("Encoding Data.csv")
 df
```
 <img width="395" height="481" alt="image" src="https://github.com/user-attachments/assets/b81327c3-efa2-4184-a4a7-cd4dc6d54f64" />
 
 ```
 from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
 pm=['Hot','Warm','Cold']
 e1=OrdinalEncoder(categories=[pm])
 e1.fit_transform(df[["ord_2"]])
 ```

<img width="213" height="254" alt="image" src="https://github.com/user-attachments/assets/1fd458c6-6d5f-40df-b2a7-4832a9e208ee" />

```
 df['bo2']=e1.fit_transform(df[["ord_2"]])
 df
```

<img width="460" height="486" alt="image" src="https://github.com/user-attachments/assets/7ffdd5ad-318e-4b2e-949d-a2485cebd831" />

```
 le=LabelEncoder()
 dfc=df.copy()
 dfc['ord_2']=le.fit_transform(dfc['ord_2'])
 dfc
```

 <img width="477" height="480" alt="image" src="https://github.com/user-attachments/assets/360f95f8-341a-49ca-992e-dca25ce9fac2" />
 
```
 from sklearn.preprocessing import OneHotEncoder
 ohe=OneHotEncoder(sparse_output=False)
 df2=df.copy()
 enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))
 df2=pd.concat([df2,enc],axis=1)
 df2
```

 <img width="608" height="483" alt="image" src="https://github.com/user-attachments/assets/52bc9da7-8610-4f05-a8f0-4acf8ca0b1af" />
 
```
 pd.get_dummies(df2,columns=["nom_0"])
```

<img width="867" height="473" alt="image" src="https://github.com/user-attachments/assets/92b43e82-d861-403c-8079-01e5b411e2e8" />

```
 from category_encoders import BinaryEncoder
 df=pd.read_csv("data.csv")
 df
```

 <img width="637" height="481" alt="image" src="https://github.com/user-attachments/assets/32194549-4843-4c01-9ba1-652534b42d7a" />
 
```
 be=BinaryEncoder()
 nd=be.fit_transform(df['Ord_2'])
 df
```

 <img width="637" height="484" alt="image" src="https://github.com/user-attachments/assets/62ff8bd5-0f4c-4eb8-9dd0-40a180d1ac9e" />
 
```
 dfb=pd.concat([df,nd],axis=1)
 dfb
```

 <img width="912" height="488" alt="image" src="https://github.com/user-attachments/assets/d4cad0a9-14c3-4f1a-af39-b710ecdd7b60" />
 
```
 from category_encoders import TargetEncoder
 te=TargetEncoder()
 CC=df.copy()
 new=te.fit_transform(X=CC["City"],y=CC["Target"])
 CC=pd.concat([CC,new],axis=1)
 CC
```

 <img width="735" height="480" alt="image" src="https://github.com/user-attachments/assets/a36213d1-0e24-4908-826b-42b433f414c1" />
 
```
 import pandas as pd
 from scipy import stats
 import numpy as np
 df=pd.read_csv("Data_to_Transform.csv")
 df
```

 <img width="1043" height="569" alt="image" src="https://github.com/user-attachments/assets/8e80fefa-9ca3-4ef7-a335-f310583fc2da" />
 
```
 df.skew()
```

 <img width="428" height="278" alt="image" src="https://github.com/user-attachments/assets/04a35e97-2b8e-4b1c-8247-e56465e97245" />
 
```
 np.log(df["Highly Positive Skew"])A
```

 <img width="394" height="613" alt="image" src="https://github.com/user-attachments/assets/4de25800-181b-4cc1-80b7-feb3de244f13" />
 
```
 np.reciprocal(df["Moderate Positive Skew"])
```

 <img width="409" height="613" alt="image" src="https://github.com/user-attachments/assets/9d8d7534-25f2-40c0-8e28-9d4ca631cc57" />
 
```
 np.sqrt(df["Highly Positive Skew"])
```

 <img width="409" height="612" alt="image" src="https://github.com/user-attachments/assets/498d3978-0a6b-4955-8f76-b2f266eeab23" />

 ```
 np.square(df["Highly Positive Skew"])
```

 <img width="379" height="616" alt="image" src="https://github.com/user-attachments/assets/2ff829e8-7203-4823-95f6-fc953df12f1e" />
 
 ```
 df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
 df
```

 <img width="1331" height="557" alt="image" src="https://github.com/user-attachments/assets/a5fb2403-c6c7-4f54-a360-ee1547a65a6a" />

 ```
 df.skew()
 ```

<img width="474" height="318" alt="image" src="https://github.com/user-attachments/assets/f17e27e5-0bcd-42ff-b69d-5a219d07cf55" />

```
 df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
 df.skew()
```
 
 <img width="517" height="365" alt="image" src="https://github.com/user-attachments/assets/cfb819f6-53cd-46de-b3d0-d5b86b219ade" />

 ```
 from sklearn.preprocessing import QuantileTransformer
 qt=QuantileTransformer(output_distribution='normal')
 df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])
 df
```

 <img width="1621" height="470" alt="image" src="https://github.com/user-attachments/assets/990db6d9-7757-4f3c-a12a-cb2b982c99b1" />
 
 
 ```
 import seaborn as sns
 import statsmodels.api as sm
 import matplotlib.pyplot as plt
 sm.qqplot(df["Moderate Negative Skew"],line='45')
 plt.show()
 ```
 
 <img width="782" height="500" alt="image" src="https://github.com/user-attachments/assets/25ae1ac1-a5f9-41f4-8e90-1e824d894d3c" />
 
 ```
 sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
 plt.show()  
 ```

 <img width="706" height="502" alt="image" src="https://github.com/user-attachments/assets/f8c2a897-acf5-46c9-a4e4-1c9fc911e7eb" />
 
 ```
 from sklearn.preprocessing import QuantileTransformer
 qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
 df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
 sm.qqplot(df["Moderate Negative Skew"],line='45')
 plt.show()
```
 
 <img width="725" height="503" alt="image" src="https://github.com/user-attachments/assets/b22c9c56-8220-4579-90fd-75cbd1aaeffd" />
 
 ```
 df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
 sm.qqplot(df["Highly Negative Skew"],line='45')
 plt.show()
```

 <img width="775" height="503" alt="image" src="https://github.com/user-attachments/assets/03c086b5-1a1c-442e-9345-15cde2c9681d" />
 
 ```
 dt=pd.read_csv("titanic_dataset.csv")
 dt
```

 <img width="1300" height="465" alt="image" src="https://github.com/user-attachments/assets/4da96f05-cbdd-44a1-b491-e9cbd488b9dd" />

 ```
 from sklearn.preprocessing import QuantileTransformer
 qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
 dt["Age_1"]=qt.fit_transform(dt[["Age"]])
 sm.qqplot(dt['Age'],line='45') 
 plt.show()
```

 <img width="682" height="500" alt="image" src="https://github.com/user-attachments/assets/5dbe506d-2a5f-4c6d-a00a-d611dc7048ab" />
 
 ```
 sm.qqplot(df["Highly Negative Skew_1"],line='45')
 plt.show()
```

 <img width="722" height="497" alt="image" src="https://github.com/user-attachments/assets/cb4fa6ca-2401-4ac1-bd12-afa35f0cae66" />




# RESULT:
 
 Thus the given data, Feature Encoding, Transformation process and save the data to a file
 was performed successfully.
       
