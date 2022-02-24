SustainScapesRepo
================

## Summary

ForRichness and Richness datasets

``` r
library(tidyverse)
```

``` r
rich <- read_csv("Richness.csv")
forrich <- read_csv("ForRichness.csv")
final <- full_join(rich,forrich)
```

The median richness for all of the sites is 7, from the year 2003 to the
year 2015

## Example of one table

``` r
Summary <- final %>% 
  dplyr::filter(!is.na(MajorHab)) %>% 
  group_by(MajorHab) %>% 
  summarise(MedianRichness=mean(Richness),
            MaxRichness=max(Richness),
            MinRichness=min(Richness))
knitr::kable(Summary,digits=2,caption="Summary of number of species according to major habitats")
```

| MajorHab | MedianRichness | MaxRichness | MinRichness |
|---------:|---------------:|------------:|------------:|
|       13 |           1.00 |           2 |           0 |
|       21 |          12.40 |          21 |           3 |
|       22 |          18.50 |          42 |           9 |
|       40 |           9.53 |          32 |           2 |
|       51 |          10.25 |          18 |           3 |
|       62 |          13.94 |          33 |           0 |
|       64 |          10.03 |          33 |           1 |
|       71 |           7.87 |          22 |           1 |
|       72 |           9.40 |          42 |           1 |
|       91 |           1.50 |           2 |           1 |
|       99 |           9.00 |          18 |           4 |

Summary of number of species according to major habitats
