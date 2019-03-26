---
layout: post
title: Pandas修改数值方法
key: 20181107
tags: python pandas
---

## Pandas笔记（二）


```python
import pandas as pd
import os

os.chdir('F:\\dir')
data = pd.read_csv('Xbox 3-day auctions.csv')
data.head()
```

<!--more-->


<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>auctionid</th>
      <th>bid</th>
      <th>bidtime</th>
      <th>bidder</th>
      <th>bidderrate</th>
      <th>openbid</th>
      <th>price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>8213034705</td>
      <td>95.0</td>
      <td>2.927373</td>
      <td>jake7870</td>
      <td>0</td>
      <td>95.0</td>
      <td>117.5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>8213034705</td>
      <td>115.0</td>
      <td>2.943484</td>
      <td>davidbresler2</td>
      <td>1</td>
      <td>95.0</td>
      <td>117.5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8213034705</td>
      <td>100.0</td>
      <td>2.951285</td>
      <td>gladimacowgirl</td>
      <td>58</td>
      <td>95.0</td>
      <td>117.5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>8213034705</td>
      <td>117.5</td>
      <td>2.998947</td>
      <td>daysrus</td>
      <td>10</td>
      <td>95.0</td>
      <td>117.5</td>
    </tr>
    <tr>
      <th>4</th>
      <td>8213060420</td>
      <td>2.0</td>
      <td>0.065266</td>
      <td>donnie4814</td>
      <td>5</td>
      <td>1.0</td>
      <td>120.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
data[data.bidder == 'parakeet2004']
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>auctionid</th>
      <th>bid</th>
      <th>bidtime</th>
      <th>bidder</th>
      <th>bidderrate</th>
      <th>openbid</th>
      <th>price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>6</th>
      <td>8213060420</td>
      <td>3.00</td>
      <td>0.186539</td>
      <td>parakeet2004</td>
      <td>5</td>
      <td>1.0</td>
      <td>120.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8213060420</td>
      <td>10.00</td>
      <td>0.186690</td>
      <td>parakeet2004</td>
      <td>5</td>
      <td>1.0</td>
      <td>120.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8213060420</td>
      <td>24.99</td>
      <td>0.187049</td>
      <td>parakeet2004</td>
      <td>5</td>
      <td>1.0</td>
      <td>120.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
data[data.bidder == 'parakeet2004']['bidderrate'] = 100
```

    d:\python37\lib\site-packages\ipykernel_launcher.py:1: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      """Entry point for launching an IPython kernel.
    


```python
data[data.bidder == 'parakeet2004']
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>auctionid</th>
      <th>bid</th>
      <th>bidtime</th>
      <th>bidder</th>
      <th>bidderrate</th>
      <th>openbid</th>
      <th>price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>6</th>
      <td>8213060420</td>
      <td>3.00</td>
      <td>0.186539</td>
      <td>parakeet2004</td>
      <td>5</td>
      <td>1.0</td>
      <td>120.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8213060420</td>
      <td>10.00</td>
      <td>0.186690</td>
      <td>parakeet2004</td>
      <td>5</td>
      <td>1.0</td>
      <td>120.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8213060420</td>
      <td>24.99</td>
      <td>0.187049</td>
      <td>parakeet2004</td>
      <td>5</td>
      <td>1.0</td>
      <td>120.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.loc[data.bidder == 'parakeet2004', 'bidderrate'] = 100
```


```python
data[data.bidder == 'parakeet2004']
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>auctionid</th>
      <th>bid</th>
      <th>bidtime</th>
      <th>bidder</th>
      <th>bidderrate</th>
      <th>openbid</th>
      <th>price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>6</th>
      <td>8213060420</td>
      <td>3.00</td>
      <td>0.186539</td>
      <td>parakeet2004</td>
      <td>100</td>
      <td>1.0</td>
      <td>120.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8213060420</td>
      <td>10.00</td>
      <td>0.186690</td>
      <td>parakeet2004</td>
      <td>100</td>
      <td>1.0</td>
      <td>120.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8213060420</td>
      <td>24.99</td>
      <td>0.187049</td>
      <td>parakeet2004</td>
      <td>100</td>
      <td>1.0</td>
      <td>120.0</td>
    </tr>
  </tbody>
</table>
</div>



再例如我们更换第6行price的值


```python
data.loc[6, 'price'] = 130.0
```


```python
data[data.bidder == 'parakeet2004']
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>auctionid</th>
      <th>bid</th>
      <th>bidtime</th>
      <th>bidder</th>
      <th>bidderrate</th>
      <th>openbid</th>
      <th>price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>6</th>
      <td>8213060420</td>
      <td>3.00</td>
      <td>0.186539</td>
      <td>parakeet2004</td>
      <td>100</td>
      <td>1.0</td>
      <td>130.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8213060420</td>
      <td>10.00</td>
      <td>0.186690</td>
      <td>parakeet2004</td>
      <td>100</td>
      <td>1.0</td>
      <td>120.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8213060420</td>
      <td>24.99</td>
      <td>0.187049</td>
      <td>parakeet2004</td>
      <td>100</td>
      <td>1.0</td>
      <td>120.0</td>
    </tr>
  </tbody>
</table>
</div>



Perfect !!!
