# Skin microbiota variation in Indian families
### The present study involves seventy-two individuals from fifteen families in two geographical regions of Maharashtra, India. This study underscores the diversity and commonalities in skin microbiota composition within and between families. ###

## Generate TSE object
Create TSE object using metadata, otu table, and taxa table. 

The data uses TreeSummarizedExperiment data container. 

To generate TSE object in RStudio run the script using the following command  
```
rmarkdown::render("fam_TSE.Rmd")
```
## Dependencies
 The primary R packages are mia and miaViz
 
 For installation visit DOI: 10.18129/B9.bioc.mia and DOI: 10.18129/B9.bioc.miaViz
 
## Analysis scripts & visualisation
Use the following scripts to perform the respective analysis.

Run the analysis script in RStudio using the following command  
```
rmarkdown::render("FILENAME.Rmd")
```

- [Alpha diversity analysis](tse_alpha.Rmd) | [Figure 2](tse_alpha.md): alpha diversity estimated using Shannon diversity index for all co-factors. 
- [Beta diversity analysis](tse_beta.Rmd) | [Figure 3](tse_beta.md): PCoA and PERMANOVA analysis was carried out with confounding factors.
- [dbRDA](RDA.Rmd) | [Figure 4](RDA.md): distance-based Redundancy analysis is performed for confounding factors.
- [most prevalent microbiome](tse_core.Rmd) | [Figure 5](tse_core.md): Location-wise relative abundances of the most prevalent phyla and genera in families.
- [Inter-generational analysis](Intergeneration_analysis.Rmd) | [Figure 6](Intergeneration_analysis.md): within and between family comparison across three generations.
- [supplementary](supplementary.Rmd) | [supplementary figure 1](supplementary.md): Family-wise inter-generational analysis.

## Authors
Renuka Potbhare, Ameeta Ravikumar, Eveliina Munukkac, Richa Ashmaa and Leo Lahti

## Preprint is available at

## License
This research work is licensed under the Artistic 2.0 license
