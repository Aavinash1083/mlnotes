---
title: "KDEplot"
author: "Aavinash"
date: 2020-09-04
description: "-"
type: technical_note
draft: false
---

```python
import seaborn as sns
```


```python
rng = np.random.RandomState(0)
x = np.linspace(0, 10, 500)
y = np.cumsum(rng.randn(500, 6), 0)

```


```python
plt.plot(x, y)
plt.legend('ABCDEF', ncol=2, loc='upper left');
```


![png](KDEplot_3_0.png)



```python
for col in 'xy':
    sns.kdeplot(data[col], shade=True)
```


![png](KDEplot_4_0.png)



```python

```
