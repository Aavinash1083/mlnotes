---
title: "Column_selection"
author: "Aavinash"
date: 2020-08-12
description: "-"
type: technical_note
draft: false
---

```python
import pandas as pd
```


```python
data = pd.read_csv("glass.csv", index_col ="Type")
```


```python
first = data["Na"]
```


```python
print(first)
```

    Type
    1    13.64
    1    13.89
    1    13.53
    1    13.21
    1    13.27
         ...  
    7    14.14
    7    14.92
    7    14.36
    7    14.38
    7    14.23
    Name: Na, Length: 214, dtype: float64



```python

```
