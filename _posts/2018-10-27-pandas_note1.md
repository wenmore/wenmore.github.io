---
layout: post
title: 记一次python脚本
key: 20181027
tags: python
---

```python
import numpy as np
import pandas as pd
import math

genome = pd.read_table("MEF_plus_R1_PA_site_count_on.genome.txt",sep="\t",header=None,low_memory=False)
peak = pd.read_table("MEF_plus_fseq.npf", sep="\t", header=None, low_memory=False)
```
<!--more-->

```python
peak = peak.loc[(peak[0]=="1")]
genome = genome.loc[(genome[0]=="1")]
```


```python
out1 = open("test1.txt","w")
out2 = open("test2.txt","w")
```


```python
data = []
for i in range(peak.shape[0]):
    raw_left_boundary = peak.iloc[i][1] + 1
    raw_right_boundary = peak.iloc[i][2]
    raw_length = raw_right_boundary - raw_left_boundary + 1
    tag_information = genome.loc[(genome[1]>=raw_left_boundary) & (genome[1] <=raw_right_boundary)]
    tag_information = tag_information[[1,3]]
    tag_information.columns = ['locus','tag']
    
    if tag_information.shape[0] == 0:
        pass
    
    elif tag_information.shape[0] == 1:
        raw_tag = tag_information.iloc[0]['tag']
        peak_location = tag_information.iloc[0]['locus']
        peak_tag = raw_tag
        mode_tag = raw_tag
        mode_percent = 1
        mode_left_boundary = peak_location
        mode_right_boundary = peak_location
        mode_length = 1
        all_tag_mean = raw_tag
        all_tag_sd = 0
        all_loc_mean = raw_tag
        all_loc_sd = 0
        peak1 = list(pd.DataFrame(peak.iloc[i]).T.values.flatten())
        sub1 = [raw_tag,raw_length,peak_location,peak_tag,mode_tag,mode_percent,mode_left_boundary,mode_right_boundary,mode_length,all_tag_mean,all_tag_sd,all_loc_mean,all_loc_sd]
        result1 = peak1 + sub1
        data.append(result1)
    
    else:
        
        raw_tag = sum(tag_information["tag"])
        peak_location = tag_information.loc[tag_information["tag"]==max(tag_information["tag"])]["locus"].iloc[0]
        peak_tag = tag_information.loc[tag_information["tag"]==max(tag_information["tag"])]["tag"].iloc[0]
        
        peak2 = list(pd.DataFrame(peak.iloc[i]).T.values.flatten())
        
        for p in range(tag_information.shape[0]):
            if (sum(tag_information.iloc[0:p]["tag"])/raw_tag) > 0.05:
                break
            else:
                for k in range(tag_information.shape[0],p,-1):
                    mode_tag = sum(tag_information[p:k]["tag"])
                    mode_percent = mode_tag/raw_tag
                    mode_left_boundary = tag_information.iloc[p]["locus"]
                    mode_right_boundary = tag_information.iloc[k-1]["locus"]
                    mode_length = mode_right_boundary - mode_left_boundary + 1
                    all_tag_mean = np.mean(tag_information[p:k]["tag"])
                    all_tag_sd = np.std(tag_information[p:k]["tag"])
                    all_loc_mean = mode_tag/mode_length
                    #all_loc_sd = math.sqrt((sum(np.square(tag_information[p:k]["tag"])) - mode_length * (np.square(all_loc_mean)))/(mode_length-1))
                    all_loc_sd = "sd"
                    data2 = []
                    if mode_percent >= 0.95:
                        sub2 = [raw_tag,raw_length,peak_location,peak_tag,mode_tag,mode_percent,mode_left_boundary,mode_right_boundary,mode_length,all_tag_mean,all_tag_sd,all_loc_mean,all_loc_sd]
                        data2.append(sub2)
                        candidate_mode = pd.DataFrame(data2)
                        candidate_mode.columns = ["raw_tag","raw_length","peak_location","peak_tag","mode_tag","mode_percent","mode_left_boundary","mode_right_boundary","mode_length","all_tag_mean","all_tag_sd","all_loc_mean","all_loc_sd"]
                        candidate_mode3 = candidate_mode.iloc[candidate_mode[candidate_mode["mode_length"]==min(candidate_mode["mode_length"])].index.tolist()]
                        list_candidate_mode3 = list(candidate_mode3.values.flatten())
                        result2 = peak2 + list_candidate_mode3
                        data.append(result2)
                    else:
                        break
```


```python
pd.DataFrame(data)
```





