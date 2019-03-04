## Assignment 5: RNA-seq and differential expression
Assignment Date: Monday, March 4, 2019  
Due Date: Monday, March 11, 2019 @ 11:59pm  

### Assignment Overview

In this assignment, you will analyze gene expression data and learn how to make several kinds of plots in the environment of your choice. 
(We suggest Python or R.) **Make sure to show your work/code in your writeup!** As before, any questions about the assignment should be posted to 
[Piazza](https://piazza.com/jhu/spring2019/en601749/home).


#### Question 1. Gene Annotation Preliminaries [10 pts]

Download the annotation of build 38 of the human genome from here:
[ftp://ftp.ensembl.org/pub/release-87/gtf/homo_sapiens/Homo_sapiens.GRCh38.87.gtf.gz](ftp://ftp.ensembl.org/pub/release-87/gtf/homo_sapiens/Homo_sapiens.GRCh38.87.gtf.gz)

- Question 1a. How many annotated protein coding genes are on each autosome of the human genome? [Hint: Protein coding genes will have "gene" in the 3rd column, and contain the following text: gene\_biotype "protein\_coding"]

- Question 1b. What is the maximum, minimum, mean, and standard deviation of the span of protein coding genes? [Hint: use the genes identified in 1b]

- Question 1c. What is the maximum, minimum, mean, and standard deviation in the number of exons for protein coding genes? [Hint: you should separately consider each isoform for each protein coding gene]


#### Question 2. Time Series [10 pts]

[This file](http://schatz-lab.org/teaching/exercises/rnaseq/rnaseq.1.expression/expression.txt) contains pre-normalized expression 
values for 100 genes over 10 time points. Most genes have a stable background expression level, but some special genes show increased 
expression over the timecourse and some show decreased expression.

a. Cluster the genes using an algorithm of your choice. Which genes show increasing expression and which genes show decreasing expression, 
and how did you determine this? What is the background expression level (numerical value) and how did you determine this? 
[Hint: K-means and hierarchical clustering are common clustering algorithms you could try.]

b. Calculate the first two principal components of the expression matrix. Show the plot and color the points based on their cluster from part (a). 
Does the PC1 axis, PC2 axis, neither, or both correspond to the clustering?

c. Create a heatmap of the expression matrix. Order the genes by cluster, but keep the time points in numerical order.


#### Question 3. Sampling Simulation [10 pts]

A typical human cell has ~250,000 transcripts, and a typical bulk RNA-seq experiment may involve millions of cells. Consequently
in an RNAseq experiment you may start with trillions of RNA molecules, although your sequencer will only give a few million to billions of reads. 
Therefore your RNAseq experiment will be a small sampling of the full composition. We hope the sequences will be a representative
sample of the total population, but if your sample is very unlucky or biased it may not represent the true distribution. We will explore
this concept by sampling a small subset of transcripts (1000 to 5000) out of a much larger set (1M) so that you can evaluate this bias.

In [data1.txt](data1.txt) with 1,000,000 lines we provide an abstraction of RNA-seq data where normalization has been performed and 
the number of times a gene name occurs corresponds to the number of transcripts sequenced.

a. Randomly sample 1000 rows. Do this simulation 10 times and record the relative abundance of each of the 15 genes. Plot the mean vs. variance.

b. Do the same sampling experiment but sample 5000 rows each time. Again plot the mean vs. variance.

c. Is the variance greater in (a) or (b)?, and explain why. What is the relationship between abundance and variance? 


#### Question 4. Differential Expression [10 pts]

a. Using the file from question 3 (data1.txt) along with [data2.txt](data2.txt), randomly sample 1000 rows from each file. 
Sample 5 times for each file (this emulates making experimental replicates) and conduct a paired t-test for 
differential expression of each of the 15 genes. Which genes are significantly differentially expressed at the 0.05 level?

b. Now sample 1000 rows 10 times from each file, equivalent to making more replicates. Which genes are now significant at the 0.05 level?

c. Perform the simulations from parts a, b but sample 5000 rows each time from each file. Which genes are significant? 

d. Now examine the complete files: which genes *actually* had different relative abundance? In a few sentences, explain your results for parts a,b,c in the 
context of this information. Address replicates and the size of the random sample. If you want, you can perform additional simple simulation 
experiments with this data - describe what you did and how it informed your answer to this question.
