## Machine learning process using python

### load required packages
``` 
import numpy as np                                            # to convert data into arrays
import pandas as pd                                           # for reading data as dataframes
from sklearn.preprocessing import Imputer                     # imputing missing values
from sklearn.preprocessing import LabelEncoder, OneHotEncoder # data encoding
from sklearn.cross_validation import train_test_split         # splitting data
from sklearn.preprocessing import StandardScaler              # scaling
from sklearn.linear_model import LinearRegression             # linear regression
```
### load data: free [Rdatasets](https://vincentarelbundock.github.io/Rdatasets/datasets.html)
``` 
data = pd.read_csv('https://vincentarelbundock.github.io/Rdatasets/csv/datasets/iris.csv')
```
### Data manipulations: Feature engineering
##### Imputations
``` 
imputer = Imputer(missing_values = "NaN", strategy = "mean", axis = 0)
imputer = imputer.fit(data[ : , 1:3])
data[ : , 1:3] = imputer.transform(data[ : , 1:3])
``` 

##### Encoding categorical data
``` 
labelencoder_X = LabelEncoder()
data[ : , 4] = labelencoder_X.fit_transform(data[ : , 4])
``` 

##### Creatre dummies
``` 
onehotencoder = OneHotEncoder(categorical_features = [0])
data[ : , 1:3] = onehotencoder.fit_transform(data[ : , 1:3]).toarray()
labelencoder_Y = LabelEncoder()
data[ : , 4] =  labelencoder_Y.fit_transform(data[ : , 4])
``` 

#### Scaling
``` 
sc_X = StandardScaler()
data[ : , 1:3] = sc_X.fit_transform(data[ : , 1:3])
``` 

#### Split the datasets: train and validation/test
``` 
X_train, X_test, Y_train, Y_test = train_test_split(data[ : , 1:3], data[ : , 4] , 
                                    test_size = 0.2, random_state = 0)
``` 

### Model
#### Model specification
```
regressor = LinearRegression() # regression

```

#### Model fit
```
model_result = regressor.fit(X_train, Y_train)
```

#### Prediction
```
model_predictions = model_result.predict(X_test)
```
