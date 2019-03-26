---
layout: post
title: literaturenote
key: 20180427
tags: 文献笔记
---

A major difference between selection in cancer and selection at the human population level is that, in cancer, only a single cell type is subject to selection whereas, in an organism, selection can occur via dysfunction of any cell type. Furthermore, in cancer, damaging mutations may be more tolerated owing to dysfunction in the normal apoptotic process. Previous studies, including those of Weinhold et al.7, show that the rate of mutation in intergenic regions is greater than in coding and regulatory regions. Our analysis suggests that the observed differences in mutation rate can be explained largely, if not entirely, by potential false positive mutations from mapping errors and by differences in mutation rate relating to base-pair type and replication timing.

<!--more-->
Sequencing coverage calculations. Sequencing coverage was calculated from VarScanSomaticSNP output. This output gives cancer and normal read counts for all potential germline and somatic variants. The <u>median coverage</u> for each cancer and normal sequencing sample was determined by taking the median coverage of these variants.

<u>from</u>: Melton, C., et al. (2015). "Recurrent somatic mutations in regulatory regions of human cancer genomes." Nature Genetics 47: 710.

Data resources
We collected polymorphisms from 1000 Genomes Project Phase 1 [34], GERP scores and ultra-conserved elements from [31,33], sensitive/ultra-sensitive regions from [26], functional genomics data from ENCODE [15], highly occupied regions (HOT) from [27], and histone modifications ChIP-Seq and gene expression RNA-Seq data from REMC [49]. Cancer driver genes are the union of genes from Vogelstein et al., cancer gene consensus, and COSMIC [2,41,42]. DNA repair and actionable genes are from [43,44]. Binary protein-protein interaction network is from InWeb [50] and HINT [51]. Regulatory and phosphorylation networks are obtained from Gerstein et al. [35], and Lin et al. [37], respectively. Whole-genome somatic alterations contain 506 cancer genomes from Alexandrov et al. [38] and 64 prostate cancer samples from [39,40].

<u>from</u>: Fu, Y., et al. (2014). "FunSeq2: a framework for prioritizing noncoding regulatory variants in cancer." Genome Biology 15(10): 480.

It is widely appreciated that cancer is a disease not of individual mutations, nor of genes, but of combinations of genes acting in molecular networks corresponding to hallmark processes such as cell proliferation and apoptosis20,21.

They are also remarkably heterogeneous, such that it is very common for clinically identical patients to share no more than a single mutation2,18,19.

An increasing number of studies have successfully integrated these network databases with tumor molecular profiles to map the molecular pathways of cancer23–27.

We also studied the effect of removing mutations judged to be nonfunctional in cancer by methods such as MutationAssessor43, cancer-specific high-throughput annotation of somatic mutations (CHASM)13 and the variant effect scoring tool (VEST)44, which use features such as sequence conservation and protein structural information to assess the likely impact of mutations. Filtering mutations with these tools resulted in decreased association of NBS subtypes with patient survival in all three cancers (Fig. 7c–e, with the possible exception of VEST for ovarian tumors: Fig. 7d). Finally, we studied the effect of removing genes with long sequences or late cell-cycle replication times: both of these characteristics have been postulated to accrue high numbers of mutations that may be unrelated to tumor progression45. We found that removal of long genes substantially degraded the ability to identify ovarian and lung subtypes predictive of survival (Fig. 7d,e). However, removal of late-replicating genes had little effect and, in the case of the lung tumor cohort, actually increased predictive power (Fig. 7e).

Missense-mutation scoring. Missense mutations were scored using three methods: CHASM13, VEST44 and MutationAssessor43. CHASM and VEST use supervised machine learning to score mutations.

<u>from</u>: Hofree, M., et al. (2013). "Network-based stratification of tumor mutations." Nature Methods 10: 1108.
