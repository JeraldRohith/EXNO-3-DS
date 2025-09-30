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

# CODING 
 import pandas as pd
 df=pd.read_csv("Encoding Data.csv")
 df

# OUTPUT

    
  <img width="487" height="549" alt="image" src="https://github.com/user-attachments/assets/f97e2e09-445c-4c42-a92f-28b7946d8144" />
    

```

from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
 pm=['Hot','Warm','Cold']
 e1=OrdinalEncoder(categories=[pm])
 e1.fit_transform(df[["ord_2"]])

```

# Output:

  <img width="688" height="354" alt="image" src="https://github.com/user-attachments/assets/d194e8bf-43b9-4f74-bbdc-3993d23964d2" />
  
```
 df['bo2']=e1.fit_transform(df[["ord_2"]])
 df

```
# Output:

<img width="493" height="517" alt="image" src="https://github.com/user-attachments/assets/c787fd64-3eb6-4506-87c4-23a5be3fa1b8" />

```
 le=LabelEncoder()
 dfc=df.copy()
 dfc['ord_2']=le.fit_transform(dfc['ord_2'])
 dfc  

```
# Output:

<img width="511" height="572" alt="image" src="https://github.com/user-attachments/assets/6e5666f7-addc-4432-a34a-cb7317be50de" />

```
 from sklearn.preprocessing import OneHotEncoder
 ohe=OneHotEncoder()
 df2=df.copy()
 enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))
 df2=pd.concat([df2,enc],axis=1)
 df2

```
# Output:

<img width="923" height="604" alt="image" src="https://github.com/user-attachments/assets/0d83c278-c76d-4f2e-97d7-8507ecaa4494" />

```
pd.get_dummies(df,columns=["nom_0"])

```
# Output:

<img width="764" height="497" alt="image" src="https://github.com/user-attachments/assets/de909740-7543-489c-9b33-98da5b7933f5" />

```
!pip install --upgrade category_encoders

```
# Output:

<img width="919" height="444" alt="image" src="https://github.com/user-attachments/assets/991717bc-319e-4832-a7fc-9f194ecc57a5" />

```
from category_encoders import BinaryEncoder
df=pd.read_csv("data.csv")
df

```
# Output:

<img width="700" height="603" alt="image" src="https://github.com/user-attachments/assets/8e22a1b5-2acf-47b8-b128-3e4a9bc2c58c" />

```
 be=BinaryEncoder()
 nd=be.fit_transform(df['Ord_2'])
 df

```
# Output:

<img width="685" height="569" alt="image" src="https://github.com/user-attachments/assets/9700142e-08f5-4ab4-bf73-6150a8a0aa24" />

```
 dfb=pd.concat([df,nd],axis=1)
 dfb

```
# Output:

<img width="945" height="527" alt="image" src="https://github.com/user-attachments/assets/1ee85b95-8d7e-4bf9-a557-a83e0624e958" />

```
 from category_encoders import TargetEncoder
 te=TargetEncoder()
 CC=df.copy()
 new=te.fit_transform(X=CC["City"],y=CC["Target"])
 CC=pd.concat([CC,new],axis=1)
 CC

```
# Output:

<img width="783" height="670" alt="image" src="https://github.com/user-attachments/assets/b1dd36ee-2dc1-415b-b017-8bd0b7a2923d" />

```
 import pandas as pd
 from scipy import stats
 import numpy as np
 df=pd.read_csv("Data_to_Transform.csv")
 df

```
# Output:

<img width="1050" height="671" alt="image" src="https://github.com/user-attachments/assets/d4d59022-8395-41aa-970a-d1fcdf732bcc" />

```
 df.skew()

```
# Output:

<img width="395" height="303" alt="image" src="https://github.com/user-attachments/assets/005cea6e-c6e2-48ad-ad36-935153c4986f" />

```
np.log(df["Highly Positive Skew"])

```
# Output:
<img width="387" height="607" alt="image" src="https://github.com/user-attachments/assets/1fae85e4-3f6b-45db-824a-40106dc826e2" />
```
 np.reciprocal(df["Moderate Positive Skew"])

```
# Output:

<img width="479" height="613" alt="image" src="https://github.com/user-attachments/assets/b9d1febd-f4d2-4a12-913d-9db21e6d707d" />

```
 np.sqrt(df["Highly Positive Skew"])

```

# Output:

<img width="420" height="619" alt="image" src="https://github.com/user-attachments/assets/6595f869-d9f8-4e6f-8aa1-d7c31d5ef1e5" />

```
 np.square(df["Highly Positive Skew"])

```

# Output:

<img width="466" height="609" alt="image" src="https://github.com/user-attachments/assets/036b77cd-beb6-4e96-85a6-8609ad8743a2" />

```
  df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
  df

```

# Output:

<img width="1382" height="589" alt="image" src="https://github.com/user-attachments/assets/8aaac5e3-3662-480e-ae9b-ec14acc51a6a" />

```
df.skew()

```

# Output:

<img width="450" height="340" alt="image" src="https://github.com/user-attachments/assets/48374efb-169d-4b3e-a022-1a3ac7e5fcef" />

```
 df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
 df.skew()

```

#  Output:

<img width="972" height="392" alt="image" src="https://github.com/user-attachments/assets/41976fe4-3925-4453-9455-86c036205e0c" />

```
 from sklearn.preprocessing import QuantileTransformer
 qt=QuantileTransformer(output_distribution='normal')
 df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])
 df

```

# Output:

<img width="1394" height="663" alt="image" src="https://github.com/user-attachments/assets/a4573fc5-acdc-4705-9fec-7e515e481919" />

```
 import seaborn as sns
 import statsmodels.api as sm
 import matplotlib.pyplot as plt
 sm.qqplot(df["Moderate Negative Skew"],line='45')
 plt.show()

```

# Output:

<img width="786" height="697" alt="image" src="https://github.com/user-attachments/assets/67af6f71-24e7-49bc-9055-819640c833c3" />

```
 sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
 plt.show()

```

# Output:

<img width="799" height="626" alt="image" src="https://github.com/user-attachments/assets/7ac54711-ae35-4e28-bf65-2d049a80b1bb" />

```
 from sklearn.preprocessing import QuantileTransformer
 qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
 df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
 sm.qqplot(df["Moderate Negative Skew"],line='45')
 plt.show()

```

# Output:

<img width="795" height="701" alt="image" src="https://github.com/user-attachments/assets/ab51384b-c035-467e-8d0b-aabe9b28ac81" />

```
 df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
 sm.qqplot(df["Highly Negative Skew"],line='45')
 plt.show()

```

# Output:

<img width="798" height="654" alt="image" src="https://github.com/user-attachments/assets/ae2399af-54e9-4c2d-af84-435696bcfaba" />

```
 dt=pd.read_csv("titanic_dataset.csv")
 dt
 from sklearn.preprocessing import QuantileTransformer
 qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
 dt["Age_1"]=qt.fit_transform(dt[["Age"]])
 sm.qqplot(dt['Age'],line='45') 
 plt.show()

```

# Output:


<img width="794" height="747" alt="image" src="https://github.com/user-attachments/assets/c084da31-adde-45d7-933c-6f145e77de79" />


```

sm.qqplot(df["Highly Negative Skew_1"],line='45')
plt.show() 

```
# Output:

<img width="796" height="630" alt="image" src="https://github.com/user-attachments/assets/a5d4cc41-2f63-4132-88e5-cb23f43f1fcd" />


# RESULT:
      Thus the given data, Feature Encoding, Transformation process and save the data to a file
  was performed successfully

       
