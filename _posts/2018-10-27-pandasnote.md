---
layout: post
title: Pandas
key: 20181027
tags: Pandas note
---

### Pandas 笔记（一）


```python
import pandas as pd
import numpy as np
```

首先创建两个数据框


```python
df = pd.DataFrame(np.random.randn(6,4),index=list('abcdef'),columns=list('ABCD'))
df
```
<!--more-->



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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>1.016502</td>
      <td>-1.762491</td>
      <td>0.410063</td>
      <td>0.775265</td>
    </tr>
    <tr>
      <th>b</th>
      <td>0.589010</td>
      <td>0.366856</td>
      <td>-0.385864</td>
      <td>-0.843721</td>
    </tr>
    <tr>
      <th>c</th>
      <td>0.032898</td>
      <td>0.606561</td>
      <td>1.582772</td>
      <td>0.278106</td>
    </tr>
    <tr>
      <th>d</th>
      <td>0.492258</td>
      <td>-0.779200</td>
      <td>1.389309</td>
      <td>-0.717689</td>
    </tr>
    <tr>
      <th>e</th>
      <td>1.300629</td>
      <td>-1.557792</td>
      <td>0.490869</td>
      <td>0.693783</td>
    </tr>
    <tr>
      <th>f</th>
      <td>-0.687722</td>
      <td>-2.170631</td>
      <td>0.650997</td>
      <td>0.683901</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.shape
```




    (6, 4)




```python
df[["A","C"]]
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
      <th>A</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>1.016502</td>
      <td>0.410063</td>
    </tr>
    <tr>
      <th>b</th>
      <td>0.589010</td>
      <td>-0.385864</td>
    </tr>
    <tr>
      <th>c</th>
      <td>0.032898</td>
      <td>1.582772</td>
    </tr>
    <tr>
      <th>d</th>
      <td>0.492258</td>
      <td>1.389309</td>
    </tr>
    <tr>
      <th>e</th>
      <td>1.300629</td>
      <td>0.490869</td>
    </tr>
    <tr>
      <th>f</th>
      <td>-0.687722</td>
      <td>0.650997</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.iloc[0]
```




    A    1.016502
    B   -1.762491
    C    0.410063
    D    0.775265
    Name: a, dtype: float64




```python
df[1:5:2]
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>b</th>
      <td>0.589010</td>
      <td>0.366856</td>
      <td>-0.385864</td>
      <td>-0.843721</td>
    </tr>
    <tr>
      <th>d</th>
      <td>0.492258</td>
      <td>-0.779200</td>
      <td>1.389309</td>
      <td>-0.717689</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1 = df[1:4]
df1
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>b</th>
      <td>0.589010</td>
      <td>0.366856</td>
      <td>-0.385864</td>
      <td>-0.843721</td>
    </tr>
    <tr>
      <th>c</th>
      <td>0.032898</td>
      <td>0.606561</td>
      <td>1.582772</td>
      <td>0.278106</td>
    </tr>
    <tr>
      <th>d</th>
      <td>0.492258</td>
      <td>-0.779200</td>
      <td>1.389309</td>
      <td>-0.717689</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2 = df[2:5]
df2
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>c</th>
      <td>0.032898</td>
      <td>0.606561</td>
      <td>1.582772</td>
      <td>0.278106</td>
    </tr>
    <tr>
      <th>d</th>
      <td>0.492258</td>
      <td>-0.779200</td>
      <td>1.389309</td>
      <td>-0.717689</td>
    </tr>
    <tr>
      <th>e</th>
      <td>1.300629</td>
      <td>-1.557792</td>
      <td>0.490869</td>
      <td>0.693783</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.concat([df1,df2],axis=1,ignore_index=False,sort=True)
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>b</th>
      <td>0.589010</td>
      <td>0.366856</td>
      <td>-0.385864</td>
      <td>-0.843721</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>c</th>
      <td>0.032898</td>
      <td>0.606561</td>
      <td>1.582772</td>
      <td>0.278106</td>
      <td>0.032898</td>
      <td>0.606561</td>
      <td>1.582772</td>
      <td>0.278106</td>
    </tr>
    <tr>
      <th>d</th>
      <td>0.492258</td>
      <td>-0.779200</td>
      <td>1.389309</td>
      <td>-0.717689</td>
      <td>0.492258</td>
      <td>-0.779200</td>
      <td>1.389309</td>
      <td>-0.717689</td>
    </tr>
    <tr>
      <th>e</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.300629</td>
      <td>-1.557792</td>
      <td>0.490869</td>
      <td>0.693783</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1.reset_index(drop=True, inplace=True)
df2.reset_index(drop=True, inplace=True)
pd.concat([df1,df2],axis=1,ignore_index=False,sort=True)
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.589010</td>
      <td>0.366856</td>
      <td>-0.385864</td>
      <td>-0.843721</td>
      <td>0.032898</td>
      <td>0.606561</td>
      <td>1.582772</td>
      <td>0.278106</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.032898</td>
      <td>0.606561</td>
      <td>1.582772</td>
      <td>0.278106</td>
      <td>0.492258</td>
      <td>-0.779200</td>
      <td>1.389309</td>
      <td>-0.717689</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.492258</td>
      <td>-0.779200</td>
      <td>1.389309</td>
      <td>-0.717689</td>
      <td>1.300629</td>
      <td>-1.557792</td>
      <td>0.490869</td>
      <td>0.693783</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.concat([df1,df2],axis=0,ignore_index=False,sort=True)
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.589010</td>
      <td>0.366856</td>
      <td>-0.385864</td>
      <td>-0.843721</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.032898</td>
      <td>0.606561</td>
      <td>1.582772</td>
      <td>0.278106</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.492258</td>
      <td>-0.779200</td>
      <td>1.389309</td>
      <td>-0.717689</td>
    </tr>
    <tr>
      <th>0</th>
      <td>0.032898</td>
      <td>0.606561</td>
      <td>1.582772</td>
      <td>0.278106</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.492258</td>
      <td>-0.779200</td>
      <td>1.389309</td>
      <td>-0.717689</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1.300629</td>
      <td>-1.557792</td>
      <td>0.490869</td>
      <td>0.693783</td>
    </tr>
  </tbody>
</table>
</div>




```python
max(df1["D"])
```




    0.27810574137491306




```python
df1_1 = df1.loc[df1["D"]==max(df1["D"])]
df1_1
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>0.032898</td>
      <td>0.606561</td>
      <td>1.582772</td>
      <td>0.278106</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2_1 = df2.loc[df2["D"]==max(df2["D"])]
df2_1
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>1.300629</td>
      <td>-1.557792</td>
      <td>0.490869</td>
      <td>0.693783</td>
    </tr>
  </tbody>
</table>
</div>



for loop 给dataframe循环加入数值时list很有用


```python
list1 = list(df1_1.values.flatten())
list1
```




    [0.032897505364488586,
     0.6065607392179079,
     1.58277232510694,
     0.27810574137491306]




```python
list2 = list(df2_1.values.flatten())
list2
```




    [1.3006285703616065,
     -1.557791838317311,
     0.49086890960200363,
     0.6937830740815967]




```python
data = []
list = list1 + list2
list
```




    [0.032897505364488586,
     0.6065607392179079,
     1.58277232510694,
     0.27810574137491306,
     1.3006285703616065,
     -1.557791838317311,
     0.49086890960200363,
     0.6937830740815967]




```python
data.append(list)
data = pd.DataFrame(data)
data
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
      <th>5</th>
      <th>6</th>
      <th>7</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.032898</td>
      <td>0.606561</td>
      <td>1.582772</td>
      <td>0.278106</td>
      <td>1.300629</td>
      <td>-1.557792</td>
      <td>0.490869</td>
      <td>0.693783</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.columns=["A","B","C","D","E","F","G","H"]
data.index = ["a"]
data
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
      <th>F</th>
      <th>G</th>
      <th>H</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>0.032898</td>
      <td>0.606561</td>
      <td>1.582772</td>
      <td>0.278106</td>
      <td>1.300629</td>
      <td>-1.557792</td>
      <td>0.490869</td>
      <td>0.693783</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.to_csv('pandas.txt',header= True, index=None, sep='\t')
```
