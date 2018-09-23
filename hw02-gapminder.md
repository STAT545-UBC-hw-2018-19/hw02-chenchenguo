---
title: "Hw02_gapminder"
author: "Chenchen Guo"
date: "2018 Sep 18th"
output: 
  html_document:
    keep_md: true
---

###Bring data package gapminder and tidyverse meta-package in

```r
# Load data and function package
library(tidyverse)
```

```
## -- Attaching packages -------------------------------------------------------------------------------------------- tidyverse 1.2.1 --
```

```
## √ ggplot2 3.0.0     √ purrr   0.2.5
## √ tibble  1.4.1     √ dplyr   0.7.6
## √ tidyr   0.8.1     √ stringr 1.2.0
## √ readr   1.1.1     √ forcats 0.3.0
```

```
## -- Conflicts ----------------------------------------------------------------------------------------------- tidyverse_conflicts() --
## x dplyr::filter() masks stats::filter()
## x dplyr::lag()    masks stats::lag()
```

```r
library(gapminder)
```


###Smell test the data


```r
# Type of whole data set 
typeof(gapminder)
```

```
## [1] "list"
```

```r
# Class information of gapminder
ls(gapminder)
```

```
## [1] "continent" "country"   "gdpPercap" "lifeExp"   "pop"       "year"
```

```r
# Column and row length of gapminder showing in two ways
ncol(gapminder)
```

```
## [1] 6
```

```r
nrow(gapminder)
```

```
## [1] 1704
```

```r
length(gapminder)
```

```
## [1] 6
```

```r
length(gapminder$country)
```

```
## [1] 1704
```

```r
# Data type of each variable
typeof(gapminder$country)
```

```
## [1] "integer"
```

```r
typeof(gapminder$continent)
```

```
## [1] "integer"
```

```r
typeof(gapminder$year)
```

```
## [1] "integer"
```

```r
typeof(gapminder$lifeExp)
```

```
## [1] "double"
```

```r
typeof(gapminder$pop)
```

```
## [1] "integer"
```

```r
typeof(gapminder$gdpPercap)
```

```
## [1] "double"
```

```r
# Basic information of gapminder data set
head(gapminder)
```

```
## # A tibble: 6 x 6
##   country     continent  year lifeExp      pop gdpPercap
##   <fctr>      <fctr>    <int>   <dbl>    <int>     <dbl>
## 1 Afghanistan Asia       1952    28.8  8425333       779
## 2 Afghanistan Asia       1957    30.3  9240934       821
## 3 Afghanistan Asia       1962    32.0 10267083       853
## 4 Afghanistan Asia       1967    34.0 11537966       836
## 5 Afghanistan Asia       1972    36.1 13079460       740
## 6 Afghanistan Asia       1977    38.4 14880372       786
```

```r
str(gapminder)
```

```
## Classes 'tbl_df', 'tbl' and 'data.frame':	1704 obs. of  6 variables:
##  $ country  : Factor w/ 142 levels "Afghanistan",..: 1 1 1 1 1 1 1 1 1 1 ...
##  $ continent: Factor w/ 5 levels "Africa","Americas",..: 3 3 3 3 3 3 3 3 3 3 ...
##  $ year     : int  1952 1957 1962 1967 1972 1977 1982 1987 1992 1997 ...
##  $ lifeExp  : num  28.8 30.3 32 34 36.1 ...
##  $ pop      : int  8425333 9240934 10267083 11537966 13079460 14880372 12881816 13867957 16317921 22227415 ...
##  $ gdpPercap: num  779 821 853 836 740 ...
```

```r
summary(gapminder)
```

```
##         country        continent        year         lifeExp     
##  Afghanistan:  12   Africa  :624   Min.   :1952   Min.   :23.60  
##  Albania    :  12   Americas:300   1st Qu.:1966   1st Qu.:48.20  
##  Algeria    :  12   Asia    :396   Median :1980   Median :60.71  
##  Angola     :  12   Europe  :360   Mean   :1980   Mean   :59.47  
##  Argentina  :  12   Oceania : 24   3rd Qu.:1993   3rd Qu.:70.85  
##  Australia  :  12                  Max.   :2007   Max.   :82.60  
##  (Other)    :1632                                                
##       pop              gdpPercap       
##  Min.   :6.001e+04   Min.   :   241.2  
##  1st Qu.:2.794e+06   1st Qu.:  1202.1  
##  Median :7.024e+06   Median :  3531.8  
##  Mean   :2.960e+07   Mean   :  7215.3  
##  3rd Qu.:1.959e+07   3rd Qu.:  9325.5  
##  Max.   :1.319e+09   Max.   :113523.1  
## 
```


###Individual variables

```r
# range and size information of class-year
ye<- gapminder$year
range(ye)
```

```
## [1] 1952 2007
```

```r
length(ye)
```

```
## [1] 1704
```

```r
summary(ye)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    1952    1966    1980    1980    1993    2007
```

```r
arrange(gapminder,year)
```

```
## Warning: package 'bindrcpp' was built under R version 3.4.4
```

```
## # A tibble: 1,704 x 6
##    country     continent  year lifeExp      pop gdpPercap
##    <fctr>      <fctr>    <int>   <dbl>    <int>     <dbl>
##  1 Afghanistan Asia       1952    28.8  8425333       779
##  2 Albania     Europe     1952    55.2  1282697      1601
##  3 Algeria     Africa     1952    43.1  9279525      2449
##  4 Angola      Africa     1952    30.0  4232095      3521
##  5 Argentina   Americas   1952    62.5 17876956      5911
##  6 Australia   Oceania    1952    69.1  8691212     10040
##  7 Austria     Europe     1952    66.8  6927772      6137
##  8 Bahrain     Asia       1952    50.9   120447      9867
##  9 Bangladesh  Asia       1952    37.5 46886859       684
## 10 Belgium     Europe     1952    68.0  8730405      8343
## # ... with 1,694 more rows
```

```r
# range and size information of life-year
life<- gapminder$lifeExp
range(life)
```

```
## [1] 23.599 82.603
```

```r
length(life)
```

```
## [1] 1704
```

```r
summary(life)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   23.60   48.20   60.71   59.47   70.85   82.60
```

```r
# range and size information of class-population
po<- gapminder$pop
range(po)
```

```
## [1]      60011 1318683096
```

```r
length(po)
```

```
## [1] 1704
```

```r
summary(po)
```

```
##      Min.   1st Qu.    Median      Mean   3rd Qu.      Max. 
## 6.001e+04 2.794e+06 7.024e+06 2.960e+07 1.959e+07 1.319e+09
```

```r
# range and size information of class-gdp
gdp<-gapminder$gdpPercap
range(gdp)
```

```
## [1]    241.1659 113523.1329
```

```r
length(gdp)
```

```
## [1] 1704
```

```r
summary(gdp)
```

```
##     Min.  1st Qu.   Median     Mean  3rd Qu.     Max. 
##    241.2   1202.1   3531.8   7215.3   9325.5 113523.1
```

```r
# Distribution of lifeExp and gdpPercap
hist(gapminder$lifeExp, breaks = 12, col="grey", xlab = "LifeExpectency", main="Life expectency distribution")
```

![](hw02-gapminder_files/figure-html/unnamed-chunk-3-1.png)<!-- -->

```r
hist(gapminder$gdpPercap, breaks = 12, col = "light blue", xlab = "GDP per Cap", main = "GDPpercap distribution")
```

![](hw02-gapminder_files/figure-html/unnamed-chunk-3-2.png)<!-- -->


###Explore various plot types


```r
# Relation between lifeExp and gdpPercap
ggplot(gapminder, aes(gdpPercap, lifeExp))+
  geom_point()+
  xlab("GDPpercap")+
  ylab("LifeExp")+
  ggtitle("Scatter plot of GDP versus LifeExp")
```

![](hw02-gapminder_files/figure-html/unnamed-chunk-4-1.png)<!-- -->

```r
# Two ways of Filter out Canada and analysis on data of Canada 
# Way one: Scatter plot
can<- filter(gapminder, country=="Canada")
plot(can$year,can$lifeExp, xlab = "Year", ylab = "Life expectancy", main = "Life expectancy tendency of Canada")
```

![](hw02-gapminder_files/figure-html/unnamed-chunk-4-2.png)<!-- -->

```r
plot(can$year,can$gdpPercap, xlab = "Year", ylab = "GDPperCap", main = "GDPpercap tendency of Canada")
```

![](hw02-gapminder_files/figure-html/unnamed-chunk-4-3.png)<!-- -->

```r
# Way two
gapminder %>% 
  filter(country=="Canada") %>% 
  ggplot(aes(year, lifeExp))+
  geom_point()+
  xlab("Year")+
  ylab("LifeExp")+
  ggtitle("Life Expentancy tendency of Cananda")
```

![](hw02-gapminder_files/figure-html/unnamed-chunk-4-4.png)<!-- -->

```r
gapminder %>% 
  filter(country=="Canada") %>% 
  ggplot(aes(year, gdpPercap))+
  geom_line()+
  xlab("Year")+
  ylab("GDPpercap")+
  ggtitle("GDPpercap tendency of Cananda")
```

![](hw02-gapminder_files/figure-html/unnamed-chunk-4-5.png)<!-- -->

```r
# The distribution of Lifeexp of ASIA
asia<- filter(gapminder, continent=="Asia")

hist(asia$lifeExp,breaks = 12, col="grey", xlab = "LifeExpectency ", main="Life expectency distribution of Asia")
```

![](hw02-gapminder_files/figure-html/unnamed-chunk-4-6.png)<!-- -->

```r
gapminder %>% 
  filter(continent=="Asia") %>% 
  ggplot(aes(lifeExp))+
  geom_histogram()+
  xlab("LifeExpectency")+
  ylab("count")+
  ggtitle("Life expectency distribution of Asia")
```

```
## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.
```

![](hw02-gapminder_files/figure-html/unnamed-chunk-4-7.png)<!-- -->

```r
gapminder %>% 
  filter(continent=="Asia") %>% 
  ggplot(aes(lifeExp))+
  geom_density(fill="light blue")+
  xlab("LifeExpectency")+
  ylab("Frequency")+
  ggtitle("Life expectency distribution of Asia")
```

![](hw02-gapminder_files/figure-html/unnamed-chunk-4-8.png)<!-- -->

```r
# Boxplot of different continents populations
ggplot(gapminder, aes(x=continent, y= pop))+ 
  scale_y_log10()+
  geom_boxplot()
```

![](hw02-gapminder_files/figure-html/unnamed-chunk-4-9.png)<!-- -->

```r
ggplot(gapminder, aes(x=continent, y= pop))+ 
  scale_y_log10()+
  geom_violin()
```

![](hw02-gapminder_files/figure-html/unnamed-chunk-4-10.png)<!-- -->

```r
# Boxplot of different continents GDP
ggplot(gapminder, aes(x=continent, y= gdpPercap))+ 
  scale_y_log10()+
  geom_boxplot()
```

![](hw02-gapminder_files/figure-html/unnamed-chunk-4-11.png)<!-- -->

```r
ggplot(gapminder, aes(x=continent, y= gdpPercap))+ 
  scale_y_log10()+
  geom_violin()+
  ggtitle("Density distribution of gdp")
```

![](hw02-gapminder_files/figure-html/unnamed-chunk-4-12.png)<!-- -->

###Use filter(), select() and %>%

```r
gapminder %>% 
  select(pop,gdpPercap) %>% 
  filter(pop>2.960e+07 & gdpPercap>1000) %>% 
  ggplot(aes(pop, gdpPercap))+
  geom_point()
```

![](hw02-gapminder_files/figure-html/unnamed-chunk-5-1.png)<!-- -->

```r
gapminder %>% 
  filter(continent=="Africa" ) %>% 
  ggplot(aes(lifeExp))+
  geom_histogram(bins = 30)+
  xlab("Africa")+
  ggtitle("Life Expendency of Africa")
```

![](hw02-gapminder_files/figure-html/unnamed-chunk-5-2.png)<!-- -->

### Things Further

```r
# This way works but the content is missing
a<- filter(gapminder,country==c("Rwanda","Afghanistan"))
a
```

```
## # A tibble: 12 x 6
##    country     continent  year lifeExp      pop gdpPercap
##    <fctr>      <fctr>    <int>   <dbl>    <int>     <dbl>
##  1 Afghanistan Asia       1957    30.3  9240934       821
##  2 Afghanistan Asia       1967    34.0 11537966       836
##  3 Afghanistan Asia       1977    38.4 14880372       786
##  4 Afghanistan Asia       1987    40.8 13867957       852
##  5 Afghanistan Asia       1997    41.8 22227415       635
##  6 Afghanistan Asia       2007    43.8 31889923       975
##  7 Rwanda      Africa     1952    40.0  2534927       493
##  8 Rwanda      Africa     1962    43.0  3051242       597
##  9 Rwanda      Africa     1972    44.6  3992121       591
## 10 Rwanda      Africa     1982    46.2  5507565       882
## 11 Rwanda      Africa     1992    23.6  7290203       737
## 12 Rwanda      Africa     2002    43.4  7852401       786
```

```r
# This is the correct way to filter out this through filter function
b<- gapminder %>% 
    filter(country=="Rwanda"|country=="Afghanistan")
b
```

```
## # A tibble: 24 x 6
##    country     continent  year lifeExp      pop gdpPercap
##    <fctr>      <fctr>    <int>   <dbl>    <int>     <dbl>
##  1 Afghanistan Asia       1952    28.8  8425333       779
##  2 Afghanistan Asia       1957    30.3  9240934       821
##  3 Afghanistan Asia       1962    32.0 10267083       853
##  4 Afghanistan Asia       1967    34.0 11537966       836
##  5 Afghanistan Asia       1972    36.1 13079460       740
##  6 Afghanistan Asia       1977    38.4 14880372       786
##  7 Afghanistan Asia       1982    39.9 12881816       978
##  8 Afghanistan Asia       1987    40.8 13867957       852
##  9 Afghanistan Asia       1992    41.7 16317921       649
## 10 Afghanistan Asia       1997    41.8 22227415       635
## # ... with 14 more rows
```






