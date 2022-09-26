# PCoA analysis

## *Principal Coordinates Analysis (PCoA)*

-   Ordination method: PCoA
-   Dissimilarity measure: bray

![](Betadiversity_files/figure-markdown_strict/PCoA-1.png)

# PERMANOVA analysis

    ## 'adonis' will be deprecated: use 'adonis2' instead

    ## Permutation: free
    ## Number of permutations: 199
    ## 
    ## Terms added sequentially (first to last)
    ## 
    ##           Df SumsOfSqs MeanSqs F.Model      R2 Pr(>F)   
    ## Diet       1    0.1282  0.1282  0.6590 0.00628  0.630   
    ## Age        2    0.4884  0.2442  1.2548 0.02391  0.235   
    ## Gender     1    0.1900  0.1900  0.9764 0.00931  0.365   
    ## Location   1    3.5054  3.5054 18.0121 0.17165  0.005 **
    ## Family    14    5.9901  0.4279  2.1985 0.29332  0.005 **
    ## Residuals 52   10.1199  0.1946         0.49554          
    ## Total     71   20.4221                 1.00000          
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

# Conclusion-

Here we found that geographical location and families are significantly
associated with bacterial community composition. No significant
difference were observed in Age, Gender and Diet group.
