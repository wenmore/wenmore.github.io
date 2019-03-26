---
layout: post
title: python、perl学习笔记
key: 20180426
tags: python perl
---

### python代码如下：
```python
with open('gene1','r') as f:
        for line in f:
#               for i in range(2,22):
#                       i=str(i)
                print("grep "+line+"FMD3.genetarget.variant_function | awk '{print $1,$2,$8,$9,$10,$11,$12}' > "+line+"_FMD3")
```

<!--more-->
### python运行结果如下：
![python](https://github.com/wenmm/wenmm.github.io/blob/master/assets/images/python.JPG)

### perl代码如下：
```perl
my $file1=shift;
open(IN,"gene1")||die "$!";

while(<IN>){
        chomp;
        my @a=split /\s+/,$_;
        print "grep $_ $file1 | awk '{print \$1,\$2,\$8,\$9,\$10,\$11,\$12}' > $_\_$file1\n";
}
```

### perl运行结果如下：
![perl](https://github.com/wenmm/wenmm.github.io/blob/master/assets/images/perl.JPG)


## 读取fasta格式的几种方法
### 此处fasta格式
```
>Rosalind_7340
AGGCCTCCCAGGTAGCTGGACTGGGAGCATCCCGATCATTAGACTAAATATGGCCACGCA
TTGTGACAGCCCTGTTCCCGCCAGCTAATGCGTGTA
>Rosalind_6964
GCACCCAATTACGTCCCGGGTACCGCGGTCACAATGCGCAGACTTGAATGATAGCGTTCC
GAGCACCCACACCCCGGCTCGTGCCT
```
### 第一种
```python
with open(sys.argv[1], 'rU') as f:
  data = f.read().replace("\n","")

pattern = re.compile(r'>(?P<label>Rosalind_\d{4})\s*(?P<bases>[ACGT\s]+)')

dnastrings = collections.OrderedDict(pattern.findall(data))

print(dnastrings)
for s1 in dnastrings.keys():
	for s2 in dnastrings.keys():
```

### 第二种
```python
def parse_fasta(fasta):
    results = []
    strings = fasta.strip().split('>')

    for s in strings:
        if len(s):
            parts = s.split()
            k = parts[0]
            v = ''.join(parts[1:])
            results.append((k, v))

    return results


def overlap_graph(fasta, n):
    results = []

    dna = parse_fasta(fasta)

    for k1, v1 in dna:
        for k2, v2 in dna:
            if k1 != k2 and v1.endswith(v2[:n]):
                results.append((k1, k2))
```

