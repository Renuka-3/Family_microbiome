## Loading necessary packages

    library(dplyr)
    library(ggplot2)
    library(sf)
    library(geodata)
    library(rmapshaper)
    library(patchwork)

## Downloading data

We will be using the `geodata` package by Hijmans et al (2024). Its
function `gadm` can be used to download data from GADM.org.

The function takes the following parameters: - country: the country code
in 3-letter ISO format (although “IN” worked as well) - level: the
administrative level, with 0 being country level and 1, 2, 3 and so on
being more granular administrative units - path: where the object should
be saved, `tempdir()` is probably sufficient in most cases but it’s a
nice touch for improved reproducibility - version: “latest” being the
default, but accepts also versions “3.6”, “4.0” and “4.1” of GADM -
resolution: 1 being high level of detail and 2 being lower level of
detail

    india_0 <- geodata::gadm("IND", level = 0, version = "4.0", path = tempdir())

When data is downloaded using the `gadm` function, it is of type
“SpatVector” from `terra` (Hijmans 2024) package.

    class(india_0)

    ## [1] "SpatVector"
    ## attr(,"package")
    ## [1] "terra"

The `tidyterra` package (Hernangomez 2023) has functions such as
`geom_spatvector` that make SpatVector objects (see [Spatial Data
Science chapter on
maps](https://rspatial.org/spatial/9-maps.html#spatvector)) play nicely
for example with `ggplot2` (see tidyterra [function
reference](https://dieghernan.github.io/tidyterra/reference/ggspatvector.html)),
but we can also convert this to a more familiar sf format from the `sf`
package (Pebesma & Bivand 2023, Pebesma 2018):

    india_0_sf <- sf::st_as_sf(india_0)
    class(india_0_sf)

    ## [1] "sf"         "data.frame"

Here we want to use district level data. With India being divided into
states and states into districts, we use level 2 of GADM hierarchy:

    india_2 <- gadm("IND", level = 2, path = tempdir())
    india_2_sf <- st_as_sf(india_2)

### Caveats / Other possibilities

GADM seems to be a widely accepted solution for mapping different
countries. However, at least in the case of Finland it seems to use
outdated or, for the lack of a better word, weird administrative
divisions (see [Finland / Southern Finland / sub-divisions
page](https://gadm.org/maps/FIN/southernfinland_2.html)). This casts a
slight shade on the repository’s reliability in the case of other
countries.

Also, I’m not a fan of the licensing, that states that “the data are
freely available for academic use and other non-commercial use.
Redistribution or commercial use is not allowed without prior
permission.” This is unlike any license I have seen in open and public
data repositories and makes me wonder what the origins of GADM
geospatial datasets is. Also it is curious that Austria is the sole
exception where the data is covered by a different license: “Creative
Commons Attribution-ShareAlike 2.0 (source: Government of Austria)”

What other options are there? ESRI India seems like a logical starting
point, but their terms of use are restrictive: Layers are “intended to
support online visualization and analysis” and “Users are not permitted
to export data for offline use.” ([Arcgis.com: India Administrative
Boundaries
2024](https://www.arcgis.com/home/item.html?id=ee1dfe59e66d48829d95bd00de6816bd))

Official Indian State GIS portal
[Bharatmaps](https://bharatmaps.gov.in/bharatmaps/#portals) seems like a
good place to look for datasets, but I could not find any datasets to
download.

data.gov.in website offers [Admin
boundaries](https://www.data.gov.in/catalog/admin-boundaries) dataset,
although it is unclear whether the dataset contained only “Boundaries
for State Capitals”. However, the dataset was not available for download
without registration, so I did not try to use it.

A group called [Development Data Lab](https://www.devdatalab.org/) has
released a dataset called SHRUG 2.0 (short for “Socioeconomic
High-resolution Rural-Urban Geographic Platform for India”) which offers
polygons used in 2011 population census, along with other nice datasets.
Clear guidelines for [citing the
data](https://docs.devdatalab.org/Getting-Started/citation/) are
provided.

Due to it being by far the easiest option, I decided to simply use the
GADM datasets.

## Taking a glance

We can use the `ggplot2` package (Wickham 2016) for visualisation:

    ggplot(india_2_sf) + geom_sf()

![](India_maps_files/figure-markdown_strict/unnamed-chunk-25-1.png)

We quickly notice that the map is very detailed - especially the South
24 Parganas Sundarbans mangrove area:

    poly <- data.frame(lon = c(87.5, 90.0),
                       lat = c(21, 23.5)) %>% 
      st_as_sf(coords = c("lon", "lat"), 
               crs = 4326) %>% 
      st_bbox() %>% 
      st_as_sfc()

    zoomed_in <- india_2_sf %>%
        st_intersection(poly)

    ## Warning: attribute variables are assumed to be spatially constant throughout all geometries

    ggplot(zoomed_in) + geom_sf()

![](India_maps_files/figure-markdown_strict/unnamed-chunk-26-1.png)

(See Jindra Lacko’s [answer on
StackOverflow](https://stackoverflow.com/questions/73264715/zooming-into-region-in-pacific)
for more details about clipping and zooming)

This is sometimes good but for a country-level map it looks just messy.

Geocomputation with R book has a chapter on [Geometric operations on
vector
data](https://bookdown.org/robinlovelace/geocompr/geometric-operations.html),
which is exactly what we want to achieve in this situation.

The `sf` package has a function called `st_simplify` which has the right
idea - see the above mentioned book chapter for caveats. Another package
called `rmapshaper` (Teucher & Russell 2023) has a function that is spot
on for our purposes:

    india_2_simpl <- ms_simplify(india_2_sf, keep = 0.001, keep_shapes = FALSE)
    ggplot(india_2_simpl) + geom_sf()

![](India_maps_files/figure-markdown_strict/unnamed-chunk-27-1.png)

Bingo! As an added benefit (or caveat), the simplification process has
simplified away the small islands on the coast of Kerala and Andaman and
Nicobar islands, making for a cleaner print at least. Therefore, use
this function with caution.

See also WZB Data Science Blog’s post on [Simplifying geospatial
features in R with sf and
rmapshaper](https://datascience.blog.wzb.eu/2021/03/15/simplifying-geospatial-features-in-r-with-sf-and-rmapshaper/)
for more information.

## Merging areas together

The easiest way to combine polygons together is to use tidyverse
functions. The `sf` package has functions `st_union` and `st_combine`
but I would say: Don’t bother. Just use `dplyr` like this:

    # NAME_1 is state name
    india_2_simpl_sums <- india_2_simpl %>% 
        group_by(NAME_1) %>% 
        summarize()

    ggplot(india_2_simpl_sums) + geom_sf()

![](India_maps_files/figure-markdown_strict/unnamed-chunk-29-1.png)

Thanks for Jindra Lacko’s blog post [Merging geometry of sf objects in
R](https://www.jla-data.net/eng/merging-geometry-of-sf-objects-in-r/)
explaining the details of this.

## Adding custom colours

There are many ways to add colours to ggplot2 visualisations and it’s
good practice to use colour palettes that are accessible for example to
colour-blind people.

If there are already defined colours that we want to use in our plot, I
will demonstrate one way to do it. (I used macOS Digital Color Meter to
get RGB values from the picture and <https://www.rgbtohex.net> website
to turn these values into Hex)

First, let’s add the basic colour for all states:

    # A type of gray
    india_2_simpl_sums <- dplyr::mutate(india_2_simpl_sums, fill = "#E3E4E6")

Then add colour to Maharashtra state that is the focus of our interest.

    # A type of green
    india_2_simpl <- mutate(india_2_simpl, fill = ifelse(NAME_1 %in% c("Maharashtra"), "#C1E2CA", "#E3E4E6"))

Then finally add manually colours for two districts that we’re
specifically interested in:

    # Type of blue
    india_2_simpl[which(india_2_simpl$NAME_2 == "Pune"),]$fill <- "#002060"
    # Type of orange
    india_2_simpl[which(india_2_simpl$NAME_2 == "Ahmadnagar"),]$fill <- "#ED7D31"

Then defining the `scale_fill_identity()` and `aes(fill = fill)` should
do the trick, see next section.

## Preliminary plot

    p1 <- ggplot() +
      scale_fill_identity() +
      geom_sf(data = india_2_simpl_sums) +
      geom_sf(data = india_2_simpl[which(india_2_simpl$NAME_1 == "Maharashtra"),], aes(fill = fill))

Print the map:

    p1

![](India_maps_files/figure-markdown_strict/unnamed-chunk-34-1.png)

## Removing the background

It might make for a cleaner visualization if we remove the extras from
the rendered plots. A relevant concept in ggplot2 related to this is
called a theme (see [function
reference](https://ggplot2.tidyverse.org/reference/ggtheme.html)) and
completely getting rid of extra elements is called using `theme_void`.

Print the map with void theme:

    p1 + theme_void()

![](India_maps_files/figure-markdown_strict/unnamed-chunk-35-1.png)

## Potential pitfalls

### dplyr without sf

If you try to use `dplyr` operations on `sf` objects without `sf`
package being loaded, you might get the following cryptic error message:

    Error in `as_tibble()`:
    ! All columns in a tibble must be vectors.
    Column `geometry` is a `sfc_GEOMETRY/sfc` object.

The key to avoiding such messages is to load all the necessary packages
at the beginning.

### Multiple layers in ggplot2

Sometimes if you have a very simple map you can just do this:

    ggplot([DATASET_NAME]) + geom_sf()

But if you want to combine multiple objects in same output, you might
think about doing this:

    ggplot() + 
        geom_sf([DATASET_NAME_1]) +
        geom_sf([DATASET_NAME_2])

But this results in an error that is something like this:

    Error in `layer_sf()`:
    ! `mapping` must be created by `aes()`.

This can be rectified simply by explicitly naming that is the data in
the geom\_sf():

    ggplot() + 
        geom_sf(data = [DATASET_NAME_1]) +
        geom_sf(data = [DATASET_NAME_2])

Thanks for [Orlando Sabogal’s answer in
StackOverflow](https://stackoverflow.com/questions/58018950/ggplot-and-sf-for-overlaying-two-layers-of-polygons-shp)
explaining this.

### 

## References

Hernangómez D (2023). “Using the tidyverse with terra objects: the
tidyterra package.” *Journal of Open Source Software*, *8*(91), 5751.
ISSN 2475-9066, <doi:10.21105/joss.05751>
<https://doi.org/10.21105/joss.05751>,
<https://doi.org/10.21105/joss.05751>.

Hijmans RJ, Barbosa M, Ghosh A, Mandel A (2024). *geodata: Download
Geographic Data*. R package version 0.6-2,
<https://CRAN.R-project.org/package=geodata>.

Hijmans R (2024). *terra: Spatial Data Analysis*. R package version
1.7-78, <https://CRAN.R-project.org/package=terra>.

Pebesma, E., & Bivand, R. (2023). Spatial Data Science: With
Applications in R. Chapman and Hall/CRC.
<https://doi.org/10.1201/9780429459016>

Pebesma, E., 2018. Simple Features for R: Standardized Support for
Spatial Vector Data. The R Journal 10 (1), 439-446,
<https://doi.org/10.32614/RJ-2018-009>

Pedersen T (2024). *patchwork: The Composer of Plots*. R package version
1.2.0, <https://CRAN.R-project.org/package=patchwork>.

Teucher A, Russell K (2023). *rmapshaper: Client for ‘mapshaper’ for
‘Geospatial’ Operations*. R package version 0.5.0,
<https://CRAN.R-project.org/package=rmapshaper>.

Wickham, H. ggplot2: Elegant Graphics for Data Analysis. Springer-Verlag
New York, 2016.
