![](tse_core_files/figure-markdown_strict/core-1.png)

## phylum

![](tse_core_files/figure-markdown_strict/phyla-1.png)

## Most prevelent genera

    ## DataFrame with 6 rows and 8 columns
    ##                     Kingdom         Phylum               Class             Order             Family
    ##                 <character>    <character>         <character>       <character>        <character>
    ## Staphylococcus     Bacteria     Firmicutes             Bacilli        Bacillales  Staphylococcaceae
    ## Bacillus           Bacteria     Firmicutes             Bacilli        Bacillales        Bacillaceae
    ## Corynebacterium    Bacteria Actinobacteria      Actinobacteria Corynebacteriales Corynebacteriaceae
    ## Pseudomonas        Bacteria Proteobacteria Gammaproteobacteria   Pseudomonadales   Pseudomonadaceae
    ## Anaerococcus       Bacteria     Firmicutes        Tissierellia    Tissierellales   Peptoniphilaceae
    ## Dermabacter        Bacteria Actinobacteria      Actinobacteria     Micrococcales   Dermabacteraceae
    ##                           Genus      mean      median
    ##                     <character> <numeric>   <numeric>
    ## Staphylococcus   Staphylococcus 0.5085410 0.602542782
    ## Bacillus               Bacillus 0.1632725 0.003518043
    ## Corynebacterium Corynebacterium 0.0104524 0.002534649
    ## Pseudomonas         Pseudomonas 0.0917532 0.001357755
    ## Anaerococcus       Anaerococcus 0.0171431 0.000518174
    ## Dermabacter         Dermabacter 0.0037439 0.000501896

    ##  Staphylococcus        Bacillus Corynebacterium     Pseudomonas     Dermabacter    Anaerococcus 
    ##       1.0000000       0.8750000       0.7361111       0.6111111       0.4027778       0.3888889

## Most prevelent phyla

    ## DataFrame with 3 rows and 8 columns
    ##                    Kingdom         Phylum       Class       Order      Family       Genus      mean    median
    ##                <character>    <character> <character> <character> <character> <character> <numeric> <numeric>
    ## Firmicutes        Bacteria     Firmicutes          NA          NA          NA          NA 0.7302366 0.9352055
    ## Proteobacteria    Bacteria Proteobacteria          NA          NA          NA          NA 0.2380125 0.0262340
    ## Actinobacteria    Bacteria Actinobacteria          NA          NA          NA          NA 0.0315763 0.0124432

    ##                 Firmicutes             Proteobacteria             Actinobacteria Candidatus_Melainabacteria 
    ##                  1.0000000                  0.9722222                  0.9027778                  0.0000000 
    ##             Planctomycetes        Alphaproteobacteria 
    ##                  0.0000000                  0.0000000
