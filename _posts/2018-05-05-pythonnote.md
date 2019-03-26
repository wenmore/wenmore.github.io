---
layout: post
title: python note
key: 20180503
tags: python
---

## note1 
### print
print ( [ object , ...][ , sep=' ' ][ , end = '\n' ][ , file=sys.stdout] )

```python
x = 'spam'
y = 99
z = ['eggs']
print(x,y,z, sep='...', file=open('data.txt','w'))
print(open('data.txt').read())
print(x,y,z,end='!\n',sep='...')
```
<!--more-->

### if

Python代码中通常的缩进错误：
```python
x='SPAM'                             #Error: first line indented
if 'rubbery' in 'shrubbery':
    print(x * 8)
        x += 'NI'                    #Error: unexpected indentation
        if x.endswith('NI'):
            x *= 2
          print(x)                   #Error: inconsistent indentation
```
正确的缩进：
```python
x='SPAM'
if 'rubbery' in 'shrubbery':
    print(x * 8)
    x += 'NI'
    if x.endswith('NI'):
        x *= 2
        print(x)                     # Prints "SPAMNISPAMNI"
```
### python作图设置x轴文字显示不全，重叠问题
```python
import pandas as pd  
import matplotlib as mb  
import matplotlib.pyplot as plt
import numpy as np

fig = plt.figure(figsize = (10, 6))
xls = pd.read_excel('feature.xlsx',name=['Feature','Mean','p'])


plt.plot(xls.Feature,xls.Mean) 
plt.gca().set_xticklabels(np.array(xls.Feature), rotation=0)
plt.ylabel("Mean")
plt.xlabel("noncoding annotations")
ax = plt.gca()
ax2 = ax.twinx()
ax2.plot(xls.Feature, xls.p, color = 'r')
ax2.set_ylabel("P-value")
plt.gcf().set_tight_layout(True)
plt.savefig("feature.png")

```
