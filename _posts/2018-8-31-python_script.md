---
layout: post
title: python script
key: 20180831
tags: python script
---

## Python

将txt格式的fasta序列转为linux两行格式的fasta序列

第一种方法：
```bash
import os
from collections import OrderedDict
name_seq = OrderedDict()
with open ('rosalind_***.txt') as f:
  for line in f:
  line = line.strip("\n")
  if line.startswith(">"):
    name = line
    name_seq[name] = ""
   else:
    name_seq[name] += line
```
<!--more-->
第二种方法：
```bash
with open ('rosalind_***.txt','r') as f:
  s = f.readline().rstrip()
  while s:
    seq_name, seq = s[1:],''
    s = f.readline().rstrip()
    while not s.startswith('>') and s:
      seq = seq + buf
      s = f.readline().rstrip()
  ```
  
第三种方法：
```bash
dna={}
while True:
  try:
    line = input()
    if line[o] == '>':
      label = line[1:]
      dna[label]+=""
     else:
      dna[label]+=line
    except EOFError:
      break
```

### RNA Splicing
```bash
from Bio import SeqIO
from Bio.Seq import Seq
from Bio.Alphabet import generic_dna

handle = open('rosalind_splc.txt','r')
lines = list(SeqIO.parse(handle,"fasta"))
chain = lines[0]
lines = lines[1:]

introns = []
for line in lines:
  start = chain.seq.find(line.seq)
  if(start > 0):
    introns.append([start, start+len(line.seq)-1])
    print("Intron %s has been detected in %i position" % (line.seq, start+1))
    
introns.append([start, start + len(line.seq)-1])
introns.sort()

last_start = 0
ORF = seq("",generic_dna)
for intron in introns:
  ORF += chain[last_start:intron[0]]
  last_start = intron[1]+1
ORF += chain[last_start:]
print(ORF.seq.translate())
```
```bash
RNAP = """UUU F      CUU L      AUU I      GUU V
UUC F      CUC L      AUC I      GUC V
UUA L      CUA L      AUA I      GUA V
UUG L      CUG L      AUG M      GUG V
UCU S      CCU P      ACU T      GCU A
UCC S      CCC P      ACC T      GCC A
UCA S      CCA P      ACA T      GCA A
UCG S      CCG P      ACG T      GCG A
UAU Y      CAU H      AAU N      GAU D
UAC Y      CAC H      AAC N      GAC D
UAA Stop   CAA Q      AAA K      GAA E
UAG Stop   CAG Q      AAG K      GAG E
UGU C      CGU R      AGU S      GGU G
UGC C      CGC R      AGC S      GGC G
UGA Stop   CGA R      AGA R      GGA G
UGG W      CGG R      AGG R      GGG G"""

traL = RNAP.split()
traDict = dict(zip(traL[0::2], traL[1::2]))
print(traDict)

f = open('rosalind_splc.txt','r')
s = f.readlines()
f.close()

samples = {}
cur_key = ''
for elem in s:
	if elem[0] == '>':
		cur_key = elem[1:].rstrip()
		samples[cur_key] = ''
	else:
		samples[cur_key] += elem.rstrip()

a = []
for line in (samples.values()):
	a.append(line)


maincode = max(a,key=len)
a.remove(maincode)
#print('I',len(maincode),maincode)
#print('')
print(a)
for i in range(len(a)):
	maincode = maincode.replace(a[i],'')
#	print(i,len(maincode),maincode)
#	print('')

b = ''
for nucleotide in maincode:
	if nucleotide == 'T':
		nucleotide = 'U'
	b += nucleotide

decoded = ''
i = b.find('AUG')
for n in range(i, len(b), 3):
	if traDict[b[n:n+3]] == 'Stop':
#		print('Amino-acid sequence of spliced protein is:')
		print(decoded)
		break
	else:
		decoded += traDict[b[n:n+3]]
```
