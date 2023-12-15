![License-Artistic_2.0-blue](https://img.shields.io/badge/License-Artistic_2.0-blue) [![DOI](https://zenodo.org/badge/372873715.svg)](https://zenodo.org/doi/10.5281/zenodo.10297062) 

# Skin microbiota variation in Indian families
### The present study involves seventy-two individuals from fifteen families in two geographical regions of Maharashtra, India. This study underscores the diversity and commonalities in skin microbiota composition within and between families. ###

## Contents
* [Usage](#usage)
* [Dependencies & Installation](#dependencies-and-installation)
* [Generate TSE object](#generate-tse-object)
* [Analysis scripts & visualization](#analysis-scripts-and-visualization)
* [Authors](#Authors)
* [Preprint](#DOI)
* [License](#License)
* [Cite the code](#cite-the-code)

## Usage
1. Use RStudio to reproduce the research work
2. Install the primary R packages
3. Create TSE object
4. Run the analysis scripts in RStudio and see the output

## Dependencies and Installation
The primary R packages are mia and miaViz;
 For installation visit [DOI: 10.18129/B9.bioc.mia](https://www.bioconductor.org/packages/release/bioc/html/mia.html) and [DOI: 10.18129/B9.bioc.miaViz](https://www.bioconductor.org/packages/release/bioc/html/miaViz.html)


## Generate TSE object
Create TSE object using metadata, otu table, and taxa table. 

The data uses TreeSummarizedExperiment data container. 

To generate TSE object in RStudio run the script using the following command  
```
rmarkdown::render("fam_TSE.Rmd")
```
 
## Analysis scripts and visualization
To start running the respective analysis first create the TSE object and then use the following command to reproduce the analysis and generate the output file as a .md document 

```
rmarkdown::render("FILENAME.Rmd", output_format="md_document")
```

- [Alpha diversity analysis](tse_alpha.Rmd) | [Figure 2](tse_alpha.md): alpha diversity estimated using Shannon diversity index for all co-factors. 
- [Beta diversity analysis](tse_beta.Rmd) | [Figure 3](tse_beta.md): PCoA and PERMANOVA analysis was carried out with confounding factors.
- [dbRDA](RDA.Rmd) | [Figure 4](RDA.md): distance-based Redundancy analysis performed for confounding factors.
- [most prevalent microbiome](tse_core.Rmd) | [Figure 5](tse_core.md): Location-wise relative abundances of the most prevalent phyla and genera in families.
- [Inter-generational analysis](Intergeneration_analysis.Rmd) | [Figure 6](Intergeneration_analysis.md): within and between family comparison across three generations.
- [supplementary](supplementary.Rmd) | [supplementary figure 1](supplementary.md): Family-wise inter-generational analysis.

## Authors
Renuka Potbhare, Ameeta Ravikumar, Eveliina Munukka, Richa Ashma and Leo Lahti

## Preprint is available at
[![DOI](https://doi.org/10.1101/2023.12.09.570904)] 

## License
This research work is licensed under the Artistic 2.0 License. See LICENSE.txt for more information.

## Cite the code
[![DOI](https://zenodo.org/badge/372873715.svg)](https://zenodo.org/doi/10.5281/zenodo.10297062)
