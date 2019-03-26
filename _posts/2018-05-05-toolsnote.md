---
layout: post
title: 工具、文件记录
key: 20180505
tags: tools
---

### note1 gtftools:
very nice tool, gtftools can merge exon and take -1 into account when transform gtf to bed.
```bash
usage: gtftools.py [-h] [-c chromosomes] [-m merged_exon] [-e exon]
       [-i intron] [-d independent_intron] [-l gene_length]
           [-r isoform_length] [-k masked_intron] [-u UTR]
           [-s isoform] [-g gene] [-t TSS] [-w window_size] [-v]
           GTFfile
```
<!--more-->
eg:
```bash
gtftools.py -g gene.bed gencode.v19.chr_patch_hapl_scaff.annotation.gtf (gene.bed是输出名)
gtftools.py -m merged_exon.bed gencode.v19.chr_patch_hapl_scaff.annotation.gtf
```    
from: [http://www.genemine.org/tools.php](http://www.genemine.org/tools.php)

### note2 Kaviar

[Download a 2.7 GB VCF file](http://s3-us-west-2.amazonaws.com/kaviar-160204-public/Kaviar-160204-Public-hg38-trim.vcf.tar) containing allele frequencies for all variants in Kaviar for GRCh38 (hg38)

[Browse other VCF downloads](http://db.systemsbiology.net/kaviar/Kaviar.downloads.html) containing data source annotations, omitting very rare variants (compact), and/or for other versions of the reference genome.

Select the file that suits your purposes. Typically, only one of the files below is needed.

|Only variants seen > 3 times (1.1 GB each file)|[GRCh38](http://s3-us-west-2.amazonaws.com/kaviar-160204-public/Kaviar-160204-Public-hg38-trimACgt3.vcf.tar)|[hg19(GRCh37)](http://s3-us-west-2.amazonaws.com/kaviar-160204-public/Kaviar-160204-Public-hg19-trimACgt3.vcf.tar)|
| :-------- | :---- | :---- |
|All variants (2.8 GB each file)|[GRCh38](http://s3-us-west-2.amazonaws.com/kaviar-160204-public/Kaviar-160204-Public-hg38-trim.vcf.tar)|[hg19(GRCh37)](http://s3-us-west-2.amazonaws.com/kaviar-160204-public/Kaviar-160204-Public-hg19-trim.vcf.tar)|
|All variants, annotated with data sources (4.7 GB each file)|[GRCh38](http://s3-us-west-2.amazonaws.com/kaviar-160204-public/Kaviar-160204-Public-hg38.vcf.tar)|[hg19(GRCh37)](http://s3-us-west-2.amazonaws.com/kaviar-160204-public/Kaviar-160204-Public-hg19.vcf.tar)|

from : [link](http://db.systemsbiology.net/kaviar/)

### note3 some vcf website
[SIFT](http://sift.bii.a-star.edu.sg/sift4g/)

[polyphen](http://genetics.bwh.harvard.edu/pph2/)

[mutationtaster](http://www.mutationtaster.org/)

[ESP](http://evs.gs.washington.edu/EVS/)

### phyloP46way and phastCons46way
There are also two methods that show measurements of sequence conservation among the 46 vertebrate genomes. Quoting the UCSC Genome Browser:

PhastCons (which has been used in previous Conservation tracks) is a hidden Markov model-based method that estimates the probability that each nucleotide belongs to a conserved element, based on the multiple alignment. It considers not just each individual alignment column, but also its flanking columns. By contrast, phyloP separately measures conservation at individual columns, ignoring the effects of their neighbours. As a consequence, the phyloP plots have a less smooth appearance than the phastCons plots, with more “texture” at individual sites. The two methods have different strengths and weaknesses. PhastCons is sensitive to “runs” of conserved sites, and is therefore effective for picking out conserved elements. PhyloP, on the other hand, is more appropriate for evaluating signatures of selection at particular nucleotides or classes of nucleotides (e.g., third codon positions, or first positions of miRNA target sites).

https://davetang.org/muse/2012/08/07/sequence-conservation-in-vertebrates/
