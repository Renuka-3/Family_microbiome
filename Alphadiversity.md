# Alpha diversity analysis

## Estimate alpha diversities

### with respect to Family

    ## 
    ##  Kruskal-Wallis rank sum test
    ## 
    ## data:  index by factor(Family)
    ## Kruskal-Wallis chi-squared = 28.158, df = 14, p-value = 0.01356

![](alphadiversity_files/figure-markdown_strict/alpha-1.png)

### Diet

    ## 
    ##  Wilcoxon rank sum test with continuity correction
    ## 
    ## data:  index by factor(Diet)
    ## W = 363, p-value = 0.0331
    ## alternative hypothesis: true location shift is not equal to 0

![](alphadiversity_files/figure-markdown_strict/alpha%20Diet-1.png)

    ## 
    ##  Wilcoxon rank sum test with continuity correction
    ## 
    ## data:  index by factor(Diet)
    ## W = 363, p-value = 0.0331
    ## alternative hypothesis: true location shift is not equal to 0

    ## [1] 0.004 0.040 0.200 0.400

### Age

    ## 
    ##  Kruskal-Wallis rank sum test
    ## 
    ## data:  index by factor(Age)
    ## Kruskal-Wallis chi-squared = 0.65216, df = 2, p-value = 0.7217

![](alphadiversity_files/figure-markdown_strict/alpha%20age-1.png)

    ## 
    ##  Wilcoxon rank sum exact test
    ## 
    ## data:  index by factor(Age)
    ## W = 233, p-value = 0.4016
    ## alternative hypothesis: true location shift is not equal to 0

    ## 
    ##  Wilcoxon rank sum exact test
    ## 
    ## data:  index by factor(Age)
    ## W = 239, p-value = 0.6153
    ## alternative hypothesis: true location shift is not equal to 0

    ## 
    ##  Wilcoxon rank sum exact test
    ## 
    ## data:  index by factor(Age)
    ## W = 319, p-value = 0.9182
    ## alternative hypothesis: true location shift is not equal to 0

    ## [1] 0.004 0.040 0.200 0.400

### Gender

    ## 
    ##  Wilcoxon rank sum exact test
    ## 
    ## data:  index by factor(Gender)
    ## W = 674, p-value = 0.7361
    ## alternative hypothesis: true location shift is not equal to 0

![](alphadiversity_files/figure-markdown_strict/alpha%20gender-1.png)

### Geographical Location

    ## 
    ##  Wilcoxon rank sum test with continuity correction
    ## 
    ## data:  index by factor(Location)
    ## W = 652, p-value = 0.09828
    ## alternative hypothesis: true location shift is not equal to 0

![](alphadiversity_files/figure-markdown_strict/alpha%20location-1.png)![](alphadiversity_files/figure-markdown_strict/alpha%20location-2.png)

    ## [1] TRUE

    ## [1] TRUE

<table>
<thead>
<tr class="header">
<th style="text-align: left;"></th>
<th style="text-align: right;">z</th>
<th style="text-align: right;">f</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">Ahmednagar</td>
<td style="text-align: right;">0.8352419</td>
<td style="text-align: right;">0.4458016</td>
</tr>
<tr class="even">
<td style="text-align: left;">Pune</td>
<td style="text-align: right;">0.6583660</td>
<td style="text-align: right;">0.5323096</td>
</tr>
</tbody>
</table>

    ## 
    ##  Wilcoxon rank sum test with continuity correction
    ## 
    ## data:  index by factor(Location)
    ## W = 652, p-value = 0.09828
    ## alternative hypothesis: true location shift is not equal to 0

<img src="alphadiversity_files/figure-markdown_strict/diffab-1.png" width="50%" />

    ## 
    ##  Wilcoxon rank sum test with continuity correction
    ## 
    ## data:  index by factor(Location)
    ## W = 652, p-value = 0.09828
    ## alternative hypothesis: true location shift is not equal to 0

    ## [1] 0.004 0.040 0.200 0.400
