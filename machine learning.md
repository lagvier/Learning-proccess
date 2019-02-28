#### Machine learning process using python

#### load required packages
``` 
import numpy as np  # to convert data into arrays
import pandas as pd # for reading data as dataframes
from sklearn.preprocessing import Imputer # imputing missing values
```
#### load data: free [Rdatasets](https://vincentarelbundock.github.io/Rdatasets/datasets.html)
``` 
data = pd.read_csv('https://vincentarelbundock.github.io/Rdatasets/csv/datasets/iris.csv')
```
### Data manipulations
#### Imputations
imputer = Imputer(missing_values = "NaN", strategy = "mean", axis = 0)
imputer = imputer.fit(data[ : , 1:3])
data[ : , 1:3] = imputer.transform(data[ : , 1:3])

#### Encoding categorical data

