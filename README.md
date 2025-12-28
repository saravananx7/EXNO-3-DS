## EXNO-3-DS

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
       # INCimport pandas as pd

df=pd.read_csv("Encoding Data.csv") df
<img width="1020" height="555" alt="Screenshot 2025-12-28 093300" src="https://github.com/user-attachments/assets/03ab33f0-8702-41b3-a735-b02eb4da1bc9" />


from sklearn.preprocessing import LabelEncoder,OrdinalEncoder pm=['Hot','Warm','Cold'] e1=OrdinalEncoder(categories=[pm]) e1.fit_transform(df[["ord_2"]]) 
<img width="916" height="433" alt="Screenshot 2025-12-28 093317" src="https://github.com/user-attachments/assets/055a03a0-57a1-425c-997f-348d23d38135" />


df['bo2']=e1.fit_transform(df[["ord_2"]]) df
<img width="897" height="646" alt="Screenshot 2025-12-28 093337" src="https://github.com/user-attachments/assets/a320b434-3abf-40c5-8744-ac8fd1685cba" />


le=LabelEncoder() dfc=df.copy() dfc['ord_2']=le.fit_transform(dfc['ord_2']) dfc
<img width="786" height="701" alt="Screenshot 2025-12-28 093345" src="https://github.com/user-attachments/assets/2d1f3caa-cee4-41c8-98f7-dbe25bee64be" />


from sklearn.preprocessing import OneHotEncoder

ohe=OneHotEncoder(sparse_output=False)

df2=df.copy()

enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))

df2=pd.concat([df2,enc],axis=1)

df2
<img width="679" height="554" alt="Screenshot 2025-12-28 093356" src="https://github.com/user-attachments/assets/73087695-ae2f-4ef9-87e3-701ce322e6e3" />


pd.get_dummies(df2,columns=["nom_0"])
<img width="1030" height="568" alt="Screenshot 2025-12-28 093409" src="https://github.com/user-attachments/assets/ec279799-f2b9-4db5-87a2-3ad2d723f9a2" />


pip install --upgrade category_encoders
<img width="1035" height="319" alt="Screenshot 2025-12-28 093426" src="https://github.com/user-attachments/assets/77a0cada-4ea4-41e8-9a5f-e18dd374c0dc" />


from category_encoders import BinaryEncoder

df=pd.read_csv("/content/data.csv")

df
<img width="774" height="546" alt="Screenshot 2025-12-28 093438" src="https://github.com/user-attachments/assets/2130d789-2877-42fa-a88b-974447ec6520" />

be=BinaryEncoder()

nd=be.fit_transform(df['Ord_2'])

df
<img width="767" height="547" alt="Screenshot 2025-12-28 093448" src="https://github.com/user-attachments/assets/9ffe2e9b-fbde-4ac0-a0a7-6dacb7e35c3d" />


dfb=pd.concat([df,nd],axis=1)

dfb
<img width="1033" height="516" alt="Screenshot 2025-12-28 093457" src="https://github.com/user-attachments/assets/249542f0-5471-4073-b0e9-03861a683e0d" />


from category_encoders import TargetEncoder

te=TargetEncoder()

CC=df.copy()

new=te.fit_transform(X=CC["City"],y=CC["Target"])

CC=pd.concat([CC,new],axis=1)

CC
<img width="879" height="551" alt="Screenshot 2025-12-28 093508" src="https://github.com/user-attachments/assets/38a8de1b-b1f4-4871-8107-948a9520f9fa" />


import pandas as pd

from scipy import stats

import numpy as np

df=pd.read_csv("/content/Data_to_Transform.csv")

df
<img width="1036" height="519" alt="Screenshot 2025-12-28 093517" src="https://github.com/user-attachments/assets/faf58e6a-6cac-43fb-9b70-1663a6372d50" />


df.skew()

<img width="539" height="288" alt="Screenshot 2025-12-28 093528" src="https://github.com/user-attachments/assets/bebb4f80-5a1e-47ab-8010-557d414ab0bd" />

np.log(df["Highly Positive Skew"])

<img width="587" height="698" alt="Screenshot 2025-12-28 093544" src="https://github.com/user-attachments/assets/0a6bf248-8555-4b3a-ae5e-0b3fb13143cf" />

np.reciprocal(df["Moderate Positive Skew"])
<img width="666" height="726" alt="Screenshot 2025-12-28 093557" src="https://github.com/user-attachments/assets/54086dd0-5beb-4736-84bc-a527ec87224e" />

np.sqrt(df["Highly Positive Skew"])
<img width="739" height="717" alt="Screenshot 2025-12-28 093612" src="https://github.com/user-attachments/assets/fe7b7401-cd5a-4259-a1b9-997e932297ff" />


np.square(df["Highly Positive Skew"])
<img width="805" height="699" alt="Screenshot 2025-12-28 093623" src="https://github.com/user-attachments/assets/be6290a2-9e32-4697-8d08-fdf790dc9ad0" />


df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"]) df
<img width="1031" height="416" alt="Screenshot 2025-12-28 093636" src="https://github.com/user-attachments/assets/578bf433-d1ee-4dfc-bb4c-7a9b39caf857" />


df.skew()
<img width="627" height="365" alt="Screenshot 2025-12-28 093648" src="https://github.com/user-attachments/assets/be1381e2-59c7-4b34-848f-863717cecfb1" />


df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])

df.skew()
<img width="763" height="442" alt="Screenshot 2025-12-28 093657" src="https://github.com/user-attachments/assets/1132659e-3aef-48fe-904e-e84c12e0b608" />


from sklearn.preprocessing import QuantileTransformer qt=QuantileTransformer(output_distribution='normal') df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]]) df
<img width="1033" height="423" alt="Screenshot 2025-12-28 093709" src="https://github.com/user-attachments/assets/29b6a7f2-f067-404d-bf26-9d2b1e78dd93" />


import seaborn as sns

import statsmodels.api as sm

import matplotlib.pyplot as plt

sm.qqplot(df["Moderate Negative Skew"],line='45')

plt.show()
<img width="1044" height="657" alt="Screenshot 2025-12-28 093721" src="https://github.com/user-attachments/assets/14947b5e-8e07-4e7c-b9ef-4f36d8721eaa" />


sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')

plt.show()
<img width="1035" height="617" alt="Screenshot 2025-12-28 093731" src="https://github.com/user-attachments/assets/1882ba47-8056-4026-8f19-28c390a09a6e" />


from sklearn.preprocessing import QuantileTransformer

qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)

df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])

sm.qqplot(df["Moderate Negative Skew"],line='45')

plt.show()
<img width="1030" height="547" alt="Screenshot 2025-12-28 093741" src="https://github.com/user-attachments/assets/eab3fdf2-47a2-4107-9e52-0e1d09d1ffdd" />


df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])

sm.qqplot(df["Highly Negative Skew"],line='45')

plt.show()
<img width="1028" height="677" alt="Screenshot 2025-12-28 093750" src="https://github.com/user-attachments/assets/3ef1e9f7-0c9e-4b3d-a9f9-ed7f3a64c27f" />


from sklearn.preprocessing import QuantileTransformer

qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)

dt["Age_1"]=qt.fit_transform(dt[["Age"]])

sm.qqplot(dt['Age'],line='45')

plt.show()
<img width="1033" height="477" alt="Screenshot 2025-12-28 093802" src="https://github.com/user-attachments/assets/1e7a6378-1fc4-48d7-a450-d90eec0f892f" />

sm.qqplot(df["Highly Negative Skew_1"],line='45')

plt.show()
<img width="1040" height="522" alt="Screenshot 2025-12-28 093814" src="https://github.com/user-attachments/assets/9ddd3e3a-c782-41e5-ba8e-e4c3ef65fc5c" />

<img width="1039" height="703" alt="Screenshot 2025-12-28 093825" src="https://github.com/user-attachments/assets/19d4dacf-b2e4-4bc7-886c-b374d1133f57" />



# RESULT:
    Feature Encoding and Transformation process was done succesfully

       
