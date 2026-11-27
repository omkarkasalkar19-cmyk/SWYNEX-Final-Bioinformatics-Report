# SWYNEX-Final-Bioinformatics-Report
Final bioinformatics report: gene expression analysis of GSE66625
# Final Bioinformatics Report
## Exploratory Analysis of Gene Expression in NCI-H446 Small-Cell Lung Cancer Cells

**Internship:** SWYNEX Technologies  
**Task:** 4 – Final Bioinformatics Report  
**Dataset:** GSE66625  
**Organism:** *Homo sapiens*  
**Platform:** GPL16951 – Phalanx Human OneArray

---

## 1. Research Question

How do gene-expression profiles of NCI-H446 small-cell lung cancer cells differ between DMSO control samples and drug-treated samples?

The objective was to retrieve a public gene-expression dataset, organize the expression measurements, calculate descriptive statistics, visualize the data and examine similarities between samples.

## 2. Dataset Description

The dataset was retrieved from the NCBI Gene Expression Omnibus (GEO).

| Parameter | Description |
|---|---|
| GEO accession | GSE66625 |
| Cell line | NCI-H446 |
| Organism | *Homo sapiens* |
| Experimental design | Control vs drug treatment |
| Control samples | GSM1626567, GSM1626568, GSM1626569 |
| Drug-treated samples | GSM1626570, GSM1626571, GSM1626572 |
| Number of samples | 6 |
| Replicates per group | 3 |
| Platform | GPL16951 – Phalanx Human OneArray |
| Expression features | 31,741 probe-level rows |

The GEO study describes three DMSO-treated flasks and three drug-treated flasks. The identity of the drug is not specified in the available study description.

## 3. Methods

### 3.1 Data Retrieval

The GSE66625 dataset was retrieved from NCBI GEO using Python and the GEOparse package in Google Colab.

The processed expression data and sample metadata were collected and organized into a tabular expression matrix.

### 3.2 Data Organization

The expression matrix contained:

- 31,741 rows representing probe-level features.
- 6 columns representing individual samples.
- 190,446 expression measurements in total.

The dataset was checked for missing values.

### 3.3 Descriptive Statistical Analysis

Using Python and Pandas, the following statistics were calculated for each sample:

- Mean
- Median
- Standard deviation
- Minimum value
- Maximum value

The sample-level statistics were exported as `sample_statistics.csv`.

A descriptive comparison of the average probe-level values between control and drug-treated groups was also calculated.

### 3.4 Data Visualization

Two visualizations were generated using Python, Matplotlib and Seaborn.

**A. Gene Expression Distribution Boxplot**

File: `expression_boxplot.png`

The boxplot was used to examine the distribution, median, spread and potential outliers of expression measurements across the six samples.

**B. Sample-to-Sample Correlation Heatmap**

File: `sample_correlation_heatmap.png`

Pearson correlation coefficients were calculated between the six sample expression profiles and displayed as a heatmap.

This visualization was used to explore the similarity of expression profiles between samples.

## 4. Results

### 4.1 Dataset Quality and Dimensions

The expression matrix contained 31,741 probe-level features across six samples.

No missing values were detected in the six sample columns during the initial missing-value assessment.

### 4.2 Sample-Level Descriptive Statistics

| Sample | Group | Mean | Median |
|---|---|---:|---:|
| GSM1626567 | Control | 3710.40 | 438.94 |
| GSM1626568 | Control | 3756.07 | 376.26 |
| GSM1626569 | Control | 3591.26 | 394.22 |
| GSM1626570 | Drug | 3671.11 | 420.54 |
| GSM1626571 | Drug | 3570.11 | 427.57 |
| GSM1626572 | Drug | 3670.09 | 475.64 |

The mean and median values varied between individual samples, indicating variation in the distribution of probe-level measurements.

### 4.3 Group-Level Descriptive Comparison

The arithmetic mean of the probe-level values across all samples within each group was calculated.

| Group | Descriptive mean |
|---|---:|
| Control | 3685.91 |
| Drug-treated | 3637.11 |

The drug-treated group had a lower overall arithmetic mean by approximately 48.80 units (about 1.32%) compared with the control group.

This is a descriptive comparison of the available probe-level values. It does not establish that the drug caused a global reduction in gene expression.

### 4.4 Boxplot Interpretation

The boxplot provides a visual summary of expression-value distributions across the six samples.

It helps examine differences in medians, variability and potential extreme observations. These patterns can help identify samples that may require further investigation.

The plot alone cannot identify individual differentially expressed genes or establish statistical significance.

### 4.5 Correlation Heatmap Interpretation

The Pearson correlation heatmap displays pairwise similarity between sample expression profiles.

Higher correlation coefficients indicate greater linear similarity between the measured profiles, while lower coefficients indicate less similarity.

The heatmap is an exploratory assessment of sample relationships. Correlation does not establish causation, biological equivalence or statistically significant treatment effects.

## 5. Limitations

1. **Small sample size:** Only three samples were available in each experimental group, limiting statistical power and generalizability.

2. **Unknown drug identity:** The available GEO study description does not clearly identify the drug used in the experiment.

3. **Microarray data:** The dataset is based on microarray expression profiling, not RNA sequencing.

4. **Probe-level measurements:** The 31,741 rows represent probe-level features. Further platform annotation is required to interpret these measurements at the gene level.

5. **Descriptive analysis:** The current workflow calculated descriptive statistics and correlations. It did not perform an independent differential-expression analysis with multiple-testing correction.

6. **Interpretation of group means:** A mean calculated across all probes is not equivalent to a biological measure of total gene expression or a gene-level treatment effect.

7. **Correlation limitations:** Pearson correlation measures linear association and does not establish biological causation.

## 6. Conclusion

This project demonstrated a basic computational workflow for retrieving, organizing, summarizing and visualizing public microarray gene-expression data.

The analysis generated sample-level descriptive statistics, a gene-expression distribution boxplot and a sample-to-sample Pearson correlation heatmap.

The results provide an exploratory overview of the dataset and its sample-level expression patterns. However, further gene-level statistical testing, probe annotation and biological validation would be necessary before drawing conclusions about drug-associated molecular changes.

## 7. Future Scope

The analysis could be extended through:

- Probe-to-gene annotation using the GPL16951 platform information.
- Differential-expression analysis using an appropriate microarray statistical workflow such as Limma.
- Multiple-testing correction and identification of candidate differentially expressed genes.
- Functional enrichment analysis using Gene Ontology and KEGG pathways.
- Biological interpretation and validation of candidate genes.

## 8. Tools and Technologies

- Python
- Google Colab
- GEOparse
- Pandas
- NumPy
- Matplotlib
- Seaborn
- NCBI GEO

## 9. References

1. NCBI Gene Expression Omnibus. GSE66625: Gene expression difference of small cell lung cancer cell after treatment with a kind of drug.  
   https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE66625

2. NCBI Gene Expression Omnibus. GPL16951: Phalanx Human OneArray Ver. 6 Release 1.  
   https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GPL16951

3. Davis, S. GEOquery: Get data from NCBI Gene Expression Omnibus. Bioconductor.  
   https://bioconductor.org/packages/release/bioc/html/GEOquery.html

4. NCBI. GEO Overview and Data Organization.  
   https://www.ncbi.nlm.nih.gov/geo/info/overview.html

5. NCBI. About GEO2R – Differential Expression Analysis.  
   https://www.ncbi.nlm.nih.gov/geo/info/geo2r.html

---

**Report prepared as part of the SWYNEX Technologies bioinformatics internship.**
