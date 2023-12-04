# Skin microbiota variation in Indian families
## The present study involves seventy-two individuals from fifteen families in two geographical regions of Maharashtra, India. This study underscores the diversity and commonalities in skin microbiota composition within and between families. ##

### Generate TSE object
Create TSE object using metadata, otu table, and taxa table. 
The data uses TreeSummarizedExperiment data container. 
To generate TSE object in RStudio run the script using the following command  
```
rmarkdown::render("fam_TSE.Rmd")
```
### Analysis scripts & visualisation
Use the following  R scripts to perform the respective analysis.
To run the analysis script use the following command  
```
rmarkdown::render("FILENAME.Rmd")
```

- [Alpha diversity analysis](tse_alpha.Rmd) | [Figure 2](tse_alpha.md): alpha diversity estimated using Shannon diversity index for all co-factors. 
- [Beta diversity analysis](tse_beta.Rmd) | [Figure 3](tse_beta.md): PCoA and PERMANOVA analysis was carried out with confounding factors.
- [dbRDA](RDA.Rmd) | [Figure 4](RDA.md): distance-based Redundancy analysis is performed for confounding factors.
- [most prevalent microbiome](tse_core.Rmd) | [Figure 5](tse_core.md): Location-wise relative abundances of the most prevalent phyla and genera in families.
- [Inter-generational analysis](Intergeneration_analysis.Rmd) | [Figure 6](Intergeneration_analysis.md): within and between family comparison across three generations.
- [supplementary](supplementary.Rmd) | [supplementary figure 1](supplementary.md): Family-wise inter-generational analysis.

  
### Preprint available at

### License
 
