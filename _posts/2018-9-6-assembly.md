---
layout: post
title: Assembly Algorithm
key: 20180906
tags: Assembly Algorithm
---

## Two approches to short read assembly

### Overlap Layout Consensus - String Graph Assemblers
     Construct overlap graph directly from reads, eliminating redundant reads; trace path for assembly
  
#### First attempt: the shortest common superstring (scs) problem
  Imagine a modified overlap graph where each edge has cost = -(length of overlap)
  SCS corresponds to a path that visits every node once, minimizing total cost along path
  That's the Traveling Salesman Problem (TSP), which is NP-hard!
  <!--more-->
  That's the hamitonian Path problem: NP-complete
  Non-optimal superstrings can be found with a greedy algorithm, At each step, the greedy algorithm "greedily" choose longest remaining overlap, merges its source and sink
  
#### Shortest common superstring: greedy
      Greedy algorithm is not guaranteed to choose overlaps yielding SCS

### de Bruijn graph-based assemblers
     Construct k-mer graph from reads; original reads are discarded
     Trace path in graph for assembly
     
      "k-mer" is a substring of length k
      
                      S: GGCGATTCATCG                  mer:from Greek meaning "part"
           A 4-mer of S:     ATTC
        All 3-mers of S: GGC
                          GCG
                           CGA
                            GAT
                             ATT
                              TTC
                               TCA
                                CAT
                                 ATC
                                  TCG
                                  
        I'll use "k-1-mer" to refer to a substring of length k-1
        
        As usual, we start with a collection of reads, which are substring of the reference genome.
        
                   AAA,AAB,ABB,BBB,BBA
                   
        AAB is a k-mer(k=3).AA is its left k-1-mer, and AB is its right k-1-mer.
#### limitations of De Bruijn graphs
            Reads are immediately split into shorter k-mers; can't resolve repeats as well as overlap graph
            Only a very specific type of "overlap" is considered, which makes dealing with errors more complicated.
            Read coherence is lost. Some paths through De Bruijn graph are inconsistent with respect to input reads. Need to thread reads through De Bruijn graph to recover information lost when reads are fragmented into k-mers.
            
## python script

  SCS:
```bash
import itertools
def overlap(a, b, min_length=3):
  start = 0
  while True:
    start = a.find(b[:min_length], start)
    if start == -1:
      return 0
     if b.startswith(a[start:]):
      return len(a)-start
     start += 1
     
def scs(ss):
  shortest_sup = None
  for ssperm in itertools.permutations(ss):
    sup = ssperm[0]
    for i in range(len(ss)-1):
      olen = overlap(ssperm[i], ssperm[i+1], min_length=1)
      sup += ssperm[i+1][olen:]
    if shortest_suo in None or len(sup) < len(shortest_sup):
      shortest_sup = sup
  return shortest_sup
```  
