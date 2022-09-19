**Family compositions**

    library(readxl)
    FamComposition <- read_excel("Fam_composition.xlsx")
    print(FamComposition)

    ## # A tibble: 16 x 14
    ##    FamilyID `Members (N)` `Generetions (N)` ...4  ...5  `Diet (N)` ...7  `Gender (N)` ...9   `Location (N)` ...11      `Age (N)` ...13      ...14
    ##    <chr>            <dbl> <chr>             <chr> <chr> <chr>      <chr> <chr>        <chr>  <chr>          <chr>      <chr>     <chr>      <chr>
    ##  1 <NA>                NA G1                G2    G3    Vegetarian Mixed Male         Female Pune           Ahmednagar Elderly   Middle age Adult
    ##  2 A                    5 1                 2     2     5          0     2            3      0              5          1         2          2    
    ##  3 B                    3 1                 1     1     3          0     2            1      0              3          1         1          1    
    ##  4 C                    5 2                 2     1     5          0     3            2      5              0          2         2          1    
    ##  5 D                    3 1                 1     1     3          0     0            3      0              3          1         1          1    
    ##  6 E                    4 1                 2     1     0          4     2            2      0              4          2         1          1    
    ##  7 F                    5 1                 2     2     1          4     2            3      5              0          1         2          2    
    ##  8 G                    5 2                 2     1     5          0     3            2      5              0          2         2          1    
    ##  9 H                    5 2                 2     1     5          0     2            3      5              0          2         2          1    
    ## 10 I                    6 2                 2     2     6          0     3            3      6              0          2         2          2    
    ## 11 J                    5 2                 2     1     0          5     2            3      5              0          2         2          1    
    ## 12 K                    5 1                 2     2     5          0     3            2      0              5          2         1          2    
    ## 13 L                    4 1                 2     1     4          0     2            2      4              0          1         2          1    
    ## 14 M                    5 1                 2     2     5          0     2            3      5              0          1         2          2    
    ## 15 N                    5 1                 2     2     3          2     1            4      5              0          1         2          2    
    ## 16 O                    7 4                 2     1     7          0     4            3      7              0          4         2          1

**Completed tasks**

1.  Phyloseq: Create phyloseq object using metadata, OTU table and taxa
    table
2.  Beta diversity analysis: PCoA and PERMANOVA analysis was carried out
    with confounding factors such as age, gender, geographical location,
    diet and family.
3.  Hierarchial Clustering: Hierarchial Clustering carried out using
    Ward2 method.
4.  Alpha diversity analysis: alpha diversity estimated using Shannon
    diversity index for all co-factors.
5.  CST analysis: Community state types analysis performed on
    geographical location.

**ToDo**

1.  Random forest analysis for family predictions
2.  PERMANOVA analysis by adjusting P values for multiple testing

**Needs to be discuss**

1.  Data cleaning/rarefaction- Singleton removal (Currently we have 211
    singleton sequences out of 1009)
2.  Analysis pipeline- Phyloseq or TSE/mia?
3.  If TSE then what about tree??
4.  Tracing family bacterial signatures?
