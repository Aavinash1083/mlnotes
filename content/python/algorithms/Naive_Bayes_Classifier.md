---
title: "Naive_Bayes_Classifier"
author: "Aavinash"
date: 2020-09-04
description: "-"
type: technical_note
draft: false
---

```python
from sklearn.datasets import load_iris
```


```python
# save "bunch" object containing iris dataset and iits attributes
iris = load_iris()
type(iris) 
```




    sklearn.utils.Bunch




```python
print (iris.data)
iris.data.shape
```

    [[5.1 3.5 1.4 0.2]
     [4.9 3.  1.4 0.2]
     [4.7 3.2 1.3 0.2]
     [4.6 3.1 1.5 0.2]
     [5.  3.6 1.4 0.2]
     [5.4 3.9 1.7 0.4]
     [4.6 3.4 1.4 0.3]
     [5.  3.4 1.5 0.2]
     [4.4 2.9 1.4 0.2]
     [4.9 3.1 1.5 0.1]
     [5.4 3.7 1.5 0.2]
     [4.8 3.4 1.6 0.2]
     [4.8 3.  1.4 0.1]
     [4.3 3.  1.1 0.1]
     [5.8 4.  1.2 0.2]
     [5.7 4.4 1.5 0.4]
     [5.4 3.9 1.3 0.4]
     [5.1 3.5 1.4 0.3]
     [5.7 3.8 1.7 0.3]
     [5.1 3.8 1.5 0.3]
     [5.4 3.4 1.7 0.2]
     [5.1 3.7 1.5 0.4]
     [4.6 3.6 1.  0.2]
     [5.1 3.3 1.7 0.5]
     [4.8 3.4 1.9 0.2]
     [5.  3.  1.6 0.2]
     [5.  3.4 1.6 0.4]
     [5.2 3.5 1.5 0.2]
     [5.2 3.4 1.4 0.2]
     [4.7 3.2 1.6 0.2]
     [4.8 3.1 1.6 0.2]
     [5.4 3.4 1.5 0.4]
     [5.2 4.1 1.5 0.1]
     [5.5 4.2 1.4 0.2]
     [4.9 3.1 1.5 0.2]
     [5.  3.2 1.2 0.2]
     [5.5 3.5 1.3 0.2]
     [4.9 3.6 1.4 0.1]
     [4.4 3.  1.3 0.2]
     [5.1 3.4 1.5 0.2]
     [5.  3.5 1.3 0.3]
     [4.5 2.3 1.3 0.3]
     [4.4 3.2 1.3 0.2]
     [5.  3.5 1.6 0.6]
     [5.1 3.8 1.9 0.4]
     [4.8 3.  1.4 0.3]
     [5.1 3.8 1.6 0.2]
     [4.6 3.2 1.4 0.2]
     [5.3 3.7 1.5 0.2]
     [5.  3.3 1.4 0.2]
     [7.  3.2 4.7 1.4]
     [6.4 3.2 4.5 1.5]
     [6.9 3.1 4.9 1.5]
     [5.5 2.3 4.  1.3]
     [6.5 2.8 4.6 1.5]
     [5.7 2.8 4.5 1.3]
     [6.3 3.3 4.7 1.6]
     [4.9 2.4 3.3 1. ]
     [6.6 2.9 4.6 1.3]
     [5.2 2.7 3.9 1.4]
     [5.  2.  3.5 1. ]
     [5.9 3.  4.2 1.5]
     [6.  2.2 4.  1. ]
     [6.1 2.9 4.7 1.4]
     [5.6 2.9 3.6 1.3]
     [6.7 3.1 4.4 1.4]
     [5.6 3.  4.5 1.5]
     [5.8 2.7 4.1 1. ]
     [6.2 2.2 4.5 1.5]
     [5.6 2.5 3.9 1.1]
     [5.9 3.2 4.8 1.8]
     [6.1 2.8 4.  1.3]
     [6.3 2.5 4.9 1.5]
     [6.1 2.8 4.7 1.2]
     [6.4 2.9 4.3 1.3]
     [6.6 3.  4.4 1.4]
     [6.8 2.8 4.8 1.4]
     [6.7 3.  5.  1.7]
     [6.  2.9 4.5 1.5]
     [5.7 2.6 3.5 1. ]
     [5.5 2.4 3.8 1.1]
     [5.5 2.4 3.7 1. ]
     [5.8 2.7 3.9 1.2]
     [6.  2.7 5.1 1.6]
     [5.4 3.  4.5 1.5]
     [6.  3.4 4.5 1.6]
     [6.7 3.1 4.7 1.5]
     [6.3 2.3 4.4 1.3]
     [5.6 3.  4.1 1.3]
     [5.5 2.5 4.  1.3]
     [5.5 2.6 4.4 1.2]
     [6.1 3.  4.6 1.4]
     [5.8 2.6 4.  1.2]
     [5.  2.3 3.3 1. ]
     [5.6 2.7 4.2 1.3]
     [5.7 3.  4.2 1.2]
     [5.7 2.9 4.2 1.3]
     [6.2 2.9 4.3 1.3]
     [5.1 2.5 3.  1.1]
     [5.7 2.8 4.1 1.3]
     [6.3 3.3 6.  2.5]
     [5.8 2.7 5.1 1.9]
     [7.1 3.  5.9 2.1]
     [6.3 2.9 5.6 1.8]
     [6.5 3.  5.8 2.2]
     [7.6 3.  6.6 2.1]
     [4.9 2.5 4.5 1.7]
     [7.3 2.9 6.3 1.8]
     [6.7 2.5 5.8 1.8]
     [7.2 3.6 6.1 2.5]
     [6.5 3.2 5.1 2. ]
     [6.4 2.7 5.3 1.9]
     [6.8 3.  5.5 2.1]
     [5.7 2.5 5.  2. ]
     [5.8 2.8 5.1 2.4]
     [6.4 3.2 5.3 2.3]
     [6.5 3.  5.5 1.8]
     [7.7 3.8 6.7 2.2]
     [7.7 2.6 6.9 2.3]
     [6.  2.2 5.  1.5]
     [6.9 3.2 5.7 2.3]
     [5.6 2.8 4.9 2. ]
     [7.7 2.8 6.7 2. ]
     [6.3 2.7 4.9 1.8]
     [6.7 3.3 5.7 2.1]
     [7.2 3.2 6.  1.8]
     [6.2 2.8 4.8 1.8]
     [6.1 3.  4.9 1.8]
     [6.4 2.8 5.6 2.1]
     [7.2 3.  5.8 1.6]
     [7.4 2.8 6.1 1.9]
     [7.9 3.8 6.4 2. ]
     [6.4 2.8 5.6 2.2]
     [6.3 2.8 5.1 1.5]
     [6.1 2.6 5.6 1.4]
     [7.7 3.  6.1 2.3]
     [6.3 3.4 5.6 2.4]
     [6.4 3.1 5.5 1.8]
     [6.  3.  4.8 1.8]
     [6.9 3.1 5.4 2.1]
     [6.7 3.1 5.6 2.4]
     [6.9 3.1 5.1 2.3]
     [5.8 2.7 5.1 1.9]
     [6.8 3.2 5.9 2.3]
     [6.7 3.3 5.7 2.5]
     [6.7 3.  5.2 2.3]
     [6.3 2.5 5.  1.9]
     [6.5 3.  5.2 2. ]
     [6.2 3.4 5.4 2.3]
     [5.9 3.  5.1 1.8]]





    (150, 4)




```python
featuresAll=[]
features = iris.data[: , [0,1,2,3]]
features.shape
```




    (150, 4)




```python
import pandas as pd
iris1 = pd.read_csv("Iris.csv") #load the dataset
iris1.head(5)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Id</th>
      <th>SepalLengthCm</th>
      <th>SepalWidthCm</th>
      <th>PetalLengthCm</th>
      <th>PetalWidthCm</th>
      <th>Species</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>4.7</td>
      <td>3.2</td>
      <td>1.3</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>4.6</td>
      <td>3.1</td>
      <td>1.5</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>5.0</td>
      <td>3.6</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
  </tbody>
</table>
</div>




```python
# I prefer to use train_test_split for cross-validation
# This piece will prove us if we have overfitting 
X3 = iris1.iloc[:, 0:5]  
Y3 = iris1['Species']
```


```python
from sklearn.model_selection import train_test_split
X3_train, X3_test, y_train, y_test = train_test_split(X3, Y3, test_size=0.4, random_state=0)
print(" X3_train",X3_train)
print("X3_test",X3_test)
print("y_train",y_train)
print("y_test",y_test)
```

     X3_train       Id  SepalLengthCm  SepalWidthCm  PetalLengthCm  PetalWidthCm
    85    86            6.0           3.4            4.5           1.6
    30    31            4.8           3.1            1.6           0.2
    101  102            5.8           2.7            5.1           1.9
    94    95            5.6           2.7            4.2           1.3
    64    65            5.6           2.9            3.6           1.3
    ..   ...            ...           ...            ...           ...
    9     10            4.9           3.1            1.5           0.1
    103  104            6.3           2.9            5.6           1.8
    67    68            5.8           2.7            4.1           1.0
    117  118            7.7           3.8            6.7           2.2
    47    48            4.6           3.2            1.4           0.2
    
    [90 rows x 5 columns]
    X3_test       Id  SepalLengthCm  SepalWidthCm  PetalLengthCm  PetalWidthCm
    114  115            5.8           2.8            5.1           2.4
    62    63            6.0           2.2            4.0           1.0
    33    34            5.5           4.2            1.4           0.2
    107  108            7.3           2.9            6.3           1.8
    7      8            5.0           3.4            1.5           0.2
    100  101            6.3           3.3            6.0           2.5
    40    41            5.0           3.5            1.3           0.3
    86    87            6.7           3.1            4.7           1.5
    76    77            6.8           2.8            4.8           1.4
    71    72            6.1           2.8            4.0           1.3
    134  135            6.1           2.6            5.6           1.4
    51    52            6.4           3.2            4.5           1.5
    73    74            6.1           2.8            4.7           1.2
    54    55            6.5           2.8            4.6           1.5
    63    64            6.1           2.9            4.7           1.4
    37    38            4.9           3.1            1.5           0.1
    78    79            6.0           2.9            4.5           1.5
    90    91            5.5           2.6            4.4           1.2
    45    46            4.8           3.0            1.4           0.3
    16    17            5.4           3.9            1.3           0.4
    121  122            5.6           2.8            4.9           2.0
    66    67            5.6           3.0            4.5           1.5
    24    25            4.8           3.4            1.9           0.2
    8      9            4.4           2.9            1.4           0.2
    126  127            6.2           2.8            4.8           1.8
    22    23            4.6           3.6            1.0           0.2
    44    45            5.1           3.8            1.9           0.4
    97    98            6.2           2.9            4.3           1.3
    93    94            5.0           2.3            3.3           1.0
    26    27            5.0           3.4            1.6           0.4
    137  138            6.4           3.1            5.5           1.8
    84    85            5.4           3.0            4.5           1.5
    27    28            5.2           3.5            1.5           0.2
    127  128            6.1           3.0            4.9           1.8
    132  133            6.4           2.8            5.6           2.2
    59    60            5.2           2.7            3.9           1.4
    18    19            5.7           3.8            1.7           0.3
    83    84            6.0           2.7            5.1           1.6
    61    62            5.9           3.0            4.2           1.5
    92    93            5.8           2.6            4.0           1.2
    112  113            6.8           3.0            5.5           2.1
    2      3            4.7           3.2            1.3           0.2
    141  142            6.9           3.1            5.1           2.3
    43    44            5.0           3.5            1.6           0.6
    10    11            5.4           3.7            1.5           0.2
    60    61            5.0           2.0            3.5           1.0
    116  117            6.5           3.0            5.5           1.8
    144  145            6.7           3.3            5.7           2.5
    119  120            6.0           2.2            5.0           1.5
    108  109            6.7           2.5            5.8           1.8
    69    70            5.6           2.5            3.9           1.1
    135  136            7.7           3.0            6.1           2.3
    56    57            6.3           3.3            4.7           1.6
    80    81            5.5           2.4            3.8           1.1
    123  124            6.3           2.7            4.9           1.8
    133  134            6.3           2.8            5.1           1.5
    106  107            4.9           2.5            4.5           1.7
    146  147            6.3           2.5            5.0           1.9
    50    51            7.0           3.2            4.7           1.4
    147  148            6.5           3.0            5.2           2.0
    y_train 85     Iris-versicolor
    30         Iris-setosa
    101     Iris-virginica
    94     Iris-versicolor
    64     Iris-versicolor
                ...       
    9          Iris-setosa
    103     Iris-virginica
    67     Iris-versicolor
    117     Iris-virginica
    47         Iris-setosa
    Name: Species, Length: 90, dtype: object
    y_test 114     Iris-virginica
    62     Iris-versicolor
    33         Iris-setosa
    107     Iris-virginica
    7          Iris-setosa
    100     Iris-virginica
    40         Iris-setosa
    86     Iris-versicolor
    76     Iris-versicolor
    71     Iris-versicolor
    134     Iris-virginica
    51     Iris-versicolor
    73     Iris-versicolor
    54     Iris-versicolor
    63     Iris-versicolor
    37         Iris-setosa
    78     Iris-versicolor
    90     Iris-versicolor
    45         Iris-setosa
    16         Iris-setosa
    121     Iris-virginica
    66     Iris-versicolor
    24         Iris-setosa
    8          Iris-setosa
    126     Iris-virginica
    22         Iris-setosa
    44         Iris-setosa
    97     Iris-versicolor
    93     Iris-versicolor
    26         Iris-setosa
    137     Iris-virginica
    84     Iris-versicolor
    27         Iris-setosa
    127     Iris-virginica
    132     Iris-virginica
    59     Iris-versicolor
    18         Iris-setosa
    83     Iris-versicolor
    61     Iris-versicolor
    92     Iris-versicolor
    112     Iris-virginica
    2          Iris-setosa
    141     Iris-virginica
    43         Iris-setosa
    10         Iris-setosa
    60     Iris-versicolor
    116     Iris-virginica
    144     Iris-virginica
    119     Iris-virginica
    108     Iris-virginica
    69     Iris-versicolor
    135     Iris-virginica
    56     Iris-versicolor
    80     Iris-versicolor
    123     Iris-virginica
    133     Iris-virginica
    106     Iris-virginica
    146     Iris-virginica
    50     Iris-versicolor
    147     Iris-virginica
    Name: Species, dtype: object



```python
from sklearn.naive_bayes import GaussianNB
model = GaussianNB()
model = model.fit(X3_train ,y_train)
y_model = model.predict(X3_test)
y_model
```




    array(['Iris-virginica', 'Iris-versicolor', 'Iris-setosa',
           'Iris-virginica', 'Iris-setosa', 'Iris-virginica', 'Iris-setosa',
           'Iris-versicolor', 'Iris-versicolor', 'Iris-versicolor',
           'Iris-virginica', 'Iris-versicolor', 'Iris-versicolor',
           'Iris-versicolor', 'Iris-versicolor', 'Iris-setosa',
           'Iris-versicolor', 'Iris-versicolor', 'Iris-setosa', 'Iris-setosa',
           'Iris-virginica', 'Iris-versicolor', 'Iris-setosa', 'Iris-setosa',
           'Iris-virginica', 'Iris-setosa', 'Iris-setosa', 'Iris-versicolor',
           'Iris-versicolor', 'Iris-setosa', 'Iris-virginica',
           'Iris-versicolor', 'Iris-setosa', 'Iris-virginica',
           'Iris-virginica', 'Iris-versicolor', 'Iris-setosa',
           'Iris-versicolor', 'Iris-versicolor', 'Iris-versicolor',
           'Iris-virginica', 'Iris-setosa', 'Iris-virginica', 'Iris-setosa',
           'Iris-setosa', 'Iris-versicolor', 'Iris-virginica',
           'Iris-virginica', 'Iris-versicolor', 'Iris-virginica',
           'Iris-versicolor', 'Iris-virginica', 'Iris-versicolor',
           'Iris-versicolor', 'Iris-virginica', 'Iris-virginica',
           'Iris-versicolor', 'Iris-virginica', 'Iris-versicolor',
           'Iris-virginica'], dtype='<U15')




```python
from sklearn.metrics import accuracy_score
accuracy_score(y_test, y_model) 
```




    0.9666666666666667




```python

```
