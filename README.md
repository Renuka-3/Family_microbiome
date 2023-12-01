# Family microbiome
## The present study involves seventy-two individuals from fifteen families in two geographical regions of Maharashtra, India. This study underscores the diversity and commonalities in skin microbiota composition within and between families. ##

### Generate TSE object
Create TSE object using metadata, otu table and taxa table. The data uses TreeSummarizedExperiment data container. 
```bash
Fam_TSE.Rmd
```

### Analysis scripts
Primary analysis packages are mia (1.6.0) (Ernst et al., 2022) and miaViz (1.6.0) (Ernst et al., 2022)
- [Figure 2 /Alpha diversity analysis](tse_alpha.Rmd): alpha diversity estimated using Shannon diversity index for all co-factors. 
- [Figure 3 /Beta diversity analysis](tse_beta.Rmd): PCoA and PERMANOVA analysis was carry out with confounding factors.
- [Figure 4 /dbRDA](RDA.Rmd)
- [Figure 5 /most prevalent microbiome](tse_core.Rmd): Location-wise relative abundances of the most prevalent phyla and genera in families.
- [Figure 6 /Inter-generational analysis](Intergeneration_analysis.Rmd): within and between family comparison across three generations. ###
  
 ### Results
- [Figure 2 /Alpha diversity analysis](tse_alpha.md) 
- [Figure 3 /Beta diversity analysis](tse_beta.md)
- [Figure 4 /dbRDA](RDA.md)
- [Figure 5 /most prevalent microbiome](tse_core.md)
- [Figure 6 /Inter-generational analysis](Intergeneration_analysis.md)
- [Tables](tables.md): 
   1. Table1- Family data
   2. Table 2- PERMANOVA
   3. Table 3- Most prevalent genera (detection threshold=0.1%, prevalence>1%).
   4. Table 4-  Most prevalent Phyla (detection threshold=0.1%, prevalence>1%).

#### supplementary figure
- [supplementary figure 1](supplimentory.Rmd): Family-wise inter-generational analysis.
- [supplementary figure 1](supplimentory.md): Family-wise inter-generational analysis.

### Preprint available at
### Authors
#### References
- Ernst F, Shetty S, Borman T, Lahti L. 2022. mia: Microbiome analysis. R package version 1.6.0.
- Ernst F, Borman T, Lahti L. 2022. miaViz: Microbiome Analysis Plotting and Visualization. R package version 1.6.0.
 
