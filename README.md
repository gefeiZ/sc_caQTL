# sc_caQTL

Call sc_caQTL based on single cell ATAC-seq data.


Introduction
------------

A python package for **discovering sc_caQTL with single cell ATAC-seq data, without WGS or WES data**. 


Installation
------------

pip install ______

------------

### Dependencies

-   `samtools`
-   `featureCounts`
-   `GATK`
-   `picard`
-   `java`
-   `bam-readcount`
-   `Python3`
-   `Pandas`
  
------------

## Usage
------------
### Step0: 


#### Build index for mapping software STAR

#### Building Peak matrix, export barcodes for each cell types.

#### From Fastq files to Bam files; SNV calling from Bam files

Check  -   `pre.sh`


### Step1: Build SNV metadata pairs


Check  -   `usage.ipynb`

### Step 2: Conduct caQTL analysis 


Check  -   `usage.ipynb`

------------
Format of caQTL Result,

-   `SNVid`: Id of SNV, represented as CHR\_\_POS
-   `Peakid`: Peak 
-   `sample_size_Ref`, `sample_size_Alt`: number of cells in REF and ALT
    group
-   `theta_Ref`, `theta_Alt`, `mu_Ref`, `mu_Alt`, `size_Ref`,
    `size_Alt`, `prob_Ref`, `prob_Alt`: estimated parameters of ZINB for
    REF group and ALT group
-   `total_mean_Ref`, `total_mean_Alt`: mean of the REF group and ALT
    group
-   `foldChange`: fold change of mean of REF group (`total_mean_Ref`)
    with respect to mean of ALT group (`total_mean_Alt`)
-   `chi2LR1`: chi square statistic for the test
-   `pvalue`, `adjusted_pvalue`: pvalue and adjusted pvalue of the test.
    If adjusted p-value is smaller than some threshold, this SNV shows
    significant eQTL effect on the target gene





The structure should be like:
------------
    output_folder
    │   
    │
    |─── bam
    |   │─── cell_type1
    |   |   │  cell_1.bam
    |   |   │  cell_1.bam.bai
    |   |   │  cell_2.bam
    |   |   │  cell_2.bam.bai
    |   |   | ...
    |   │─── cell_type2
    |   |   │  cell_1.bam
    |   |   │  cell_1.bam.bai
    |   |   │  cell_2.bam
    |   |   │  cell_2.bam.bai
    |   |   | ...
    |
    |─── peak_matrix
    |   │─── cell_level_files
    |   |   │  cell_type1_matrix.csv
    |   |   │  cell_type2_matrix.csv
    |   |   | ...
    |   
    |─── snv
    |   |─── cell_level_snv
    |   |   |─── cell_type1
    |   |   │      cell_1_filtered_pass.vcf
    |   |   |      cell_1_filtered_pass.vcf.idx
    |   |   │      cell_2_filtered_pass.vcf
    |   |   |      cell_2_filtered_pass.vcf.idx
    |   |   | ...
    |   |   |─── cell_type2
    |   |   │      cell_1_filtered_pass.vcf
    |   |   |      cell_1_filtered_pass.vcf.idx
    |   |   │      cell_2_filtered_pass.vcf
    |   |   |      cell_2_filtered_pass.vcf.idx
    |   |   |  ...
    |   |   |
    |   |─── snv_matrix
    |   |   │  celltype1_SNV_matrix.csv
    |   |   │  celltype2_SNV_matrix.csv
    |   |   |  ...
    |   |   |
    
