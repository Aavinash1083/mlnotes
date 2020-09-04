---
title: "Decision_Tree_Classifier"
author: "Aavinash"
date: 2020-09-04
description: "-"
type: technical_note
draft: false
---

```python
import pandas as pd
import numpy as np
from sklearn.metrics import accuracy_score
import matplotlib.pyplot as plt

%matplotlib inline
```


```python
from sklearn import datasets
iris = datasets.load_iris()

X = iris.data[:,[2,3]]
Y = iris.target

print(X[1:5,:])
print(Y)  
```

    [[1.4 0.2]
     [1.3 0.2]
     [1.5 0.2]
     [1.4 0.2]]
    [0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
     0 0 0 0 0 0 0 0 0 0 0 0 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1
     1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 2 2 2 2 2 2 2 2 2 2 2
     2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2
     2 2]



```python
## 1. Splitting the dataset

from sklearn.model_selection import train_test_split
X_train, X_test, Y_train, Y_test = train_test_split(X,Y,test_size=0.3,random_state=0)

length_Train = len(X_train)
length_Test = len(X_test)

print("There are ",length_Train,"samples in the trainig set and",length_Test,"samples in the test set")
print("-----------------------------------------------------------------------------------------------")
print("")

## 2. Feature scaling.

from sklearn.preprocessing import StandardScaler
sc = StandardScaler()
sc.fit(X_train)
X_train_standard = sc.transform(X_train)
X_test_standard = sc.transform(X_test)

print("X_train without standardising features")
print("--------------------------------------")
print(X_train[1:5,:])
print("")
print("X_train standardising features")
print("--------------------------------------")
print(X_train_standard[1:5,:])
```

    There are  105 samples in the trainig set and 45 samples in the test set
    -----------------------------------------------------------------------------------------------
    
    X_train without standardising features
    --------------------------------------
    [[5.5 1.8]
     [5.7 2.5]
     [5.  1.5]
     [5.8 1.8]]
    
    X_train standardising features
    --------------------------------------
    [[0.93066067 0.7372463 ]
     [1.04202177 1.63887031]
     [0.6522579  0.35083601]
     [1.09770233 0.7372463 ]]



```python
from sklearn.tree import DecisionTreeClassifier

tree = DecisionTreeClassifier(criterion='entropy'
                             , max_depth = 3
                             , random_state = 0)
tree.fit(X_train,Y_train)
```




    DecisionTreeClassifier(criterion='entropy', max_depth=3, random_state=0)




```python
Y_pred_tree = tree.predict(X_test)

print("Accuracy: %.2f" % accuracy_score(Y_test,Y_pred_tree))
```

    Accuracy: 0.98



```python

```
