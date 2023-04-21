Sydney_property_sold_2016_2022
================
Ha Luong
4/22/2023

# Summary columns and column type

``` r
str(df)
```

    ## spc_tbl_ [11,160 × 17] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ price                   : num [1:11160] 530000 525000 480000 452000 365500 ...
    ##  $ date_sold               : Date[1:11160], format: "2016-01-13" "2016-01-13" ...
    ##  $ suburb                  : chr [1:11160] "Kincumber" "Halekulani" "Chittaway Bay" "Leumeah" ...
    ##  $ num_bath                : num [1:11160] 4 2 2 1 0 1 1 1 1 0 ...
    ##  $ num_bed                 : num [1:11160] 4 4 4 3 0 3 3 3 3 0 ...
    ##  $ num_parking             : num [1:11160] 2 2 2 1 0 1 1 2 3 0 ...
    ##  $ property_size           : num [1:11160] 1351 594 468 344 1850 ...
    ##  $ type                    : chr [1:11160] "House" "House" "House" "House" ...
    ##  $ suburb_population       : num [1:11160] 7093 2538 2028 9835 2200 ...
    ##  $ suburb_median_income    : num [1:11160] 29432 24752 31668 32292 45084 ...
    ##  $ suburb_sqkm             : num [1:11160] 9.91 1.4 1.12 4.05 1.5 ...
    ##  $ suburb_lat              : num [1:11160] -33.5 -33.2 -33.3 -34.1 -33.5 ...
    ##  $ suburb_lng              : num [1:11160] 151 152 151 151 151 ...
    ##  $ suburb_elevation        : num [1:11160] 24 23 3 81 18 24 27 81 4 263 ...
    ##  $ cash_rate               : num [1:11160] 2 2 2 2 2 2 2 2 2 2 ...
    ##  $ property_inflation_index: num [1:11160] 151 151 151 151 151 ...
    ##  $ km_from_cbd             : num [1:11160] 47 78.5 63.6 40.1 50 ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   price = col_double(),
    ##   ..   date_sold = col_date(format = ""),
    ##   ..   suburb = col_character(),
    ##   ..   num_bath = col_double(),
    ##   ..   num_bed = col_double(),
    ##   ..   num_parking = col_double(),
    ##   ..   property_size = col_double(),
    ##   ..   type = col_character(),
    ##   ..   suburb_population = col_double(),
    ##   ..   suburb_median_income = col_double(),
    ##   ..   suburb_sqkm = col_double(),
    ##   ..   suburb_lat = col_double(),
    ##   ..   suburb_lng = col_double(),
    ##   ..   suburb_elevation = col_double(),
    ##   ..   cash_rate = col_double(),
    ##   ..   property_inflation_index = col_double(),
    ##   ..   km_from_cbd = col_double()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr>

Create column “year” from column date_sold to analyze by year

``` r
df$year <- format(df$date_sold, format="%Y")
```

# Cleaning data

## Summary data

``` r
summary(df)
```

    ##      price            date_sold             suburb             num_bath     
    ##  Min.   :  225000   Min.   :2016-01-13   Length:11160       Min.   : 0.000  
    ##  1st Qu.: 1002000   1st Qu.:2018-10-18   Class :character   1st Qu.: 1.000  
    ##  Median : 1388000   Median :2020-11-24   Mode  :character   Median : 2.000  
    ##  Mean   : 1675395   Mean   :2020-03-11                      Mean   : 2.074  
    ##  3rd Qu.: 2020000   3rd Qu.:2021-10-11                      3rd Qu.: 3.000  
    ##  Max.   :60000000   Max.   :2022-01-01                      Max.   :46.000  
    ##     num_bed        num_parking     property_size       type          
    ##  Min.   : 0.000   Min.   : 0.000   Min.   :    7   Length:11160      
    ##  1st Qu.: 3.000   1st Qu.: 1.000   1st Qu.:  430   Class :character  
    ##  Median : 4.000   Median : 2.000   Median :  600   Mode  :character  
    ##  Mean   : 3.759   Mean   : 2.017   Mean   :  723                     
    ##  3rd Qu.: 4.000   3rd Qu.: 2.000   3rd Qu.:  765                     
    ##  Max.   :47.000   Max.   :50.000   Max.   :59100                     
    ##  suburb_population suburb_median_income  suburb_sqkm       suburb_lat    
    ##  Min.   :   22     Min.   :14248        Min.   : 0.089   Min.   :-34.11  
    ##  1st Qu.: 3977     1st Qu.:32448        1st Qu.: 1.776   1st Qu.:-33.92  
    ##  Median : 7457     Median :39104        Median : 3.566   Median :-33.81  
    ##  Mean   : 9312     Mean   :40168        Mean   : 5.055   Mean   :-33.78  
    ##  3rd Qu.:12158     3rd Qu.:45552        3rd Qu.: 6.568   3rd Qu.:-33.72  
    ##  Max.   :47176     Max.   :97500        Max.   :87.154   Max.   :-33.16  
    ##    suburb_lng    suburb_elevation   cash_rate      property_inflation_index
    ##  Min.   :150.6   Min.   :  0.00   Min.   :0.1000   Min.   :150.9           
    ##  1st Qu.:151.0   1st Qu.: 21.00   1st Qu.:0.1000   1st Qu.:167.6           
    ##  Median :151.1   Median : 40.00   Median :0.1100   Median :176.6           
    ##  Mean   :151.1   Mean   : 55.61   Mean   :0.6314   Mean   :188.5           
    ##  3rd Qu.:151.2   3rd Qu.: 75.00   3rd Qu.:1.5000   3rd Qu.:220.1           
    ##  Max.   :151.6   Max.   :405.00   Max.   :2.0000   Max.   :220.1           
    ##   km_from_cbd        year          
    ##  Min.   : 0.31   Length:11160      
    ##  1st Qu.:12.96   Class :character  
    ##  Median :22.31   Mode  :character  
    ##  Mean   :27.38                     
    ##  3rd Qu.:40.99                     
    ##  Max.   :84.79

## Check for inappropriate data and outliner, elimitate outliners using Empirical rule (House Price \> 5.540.000 AUD, number of bed \> 9, number of bath \> 6)

``` r
mean(df$num_bed)
```

    ## [1] 3.758961

``` r
sd(df$num_bed)
```

    ## [1] 1.559743

``` r
mean(df$num_bath)
```

    ## [1] 2.073566

``` r
sd(df$num_bath)
```

    ## [1] 1.184881

``` r
cleaned_df <- df[!(df$price > 5540000) & !(df$num_bed >9) & !(df$num_bath > 6),]
str(cleaned_df)
```

    ## tibble [10,945 × 18] (S3: tbl_df/tbl/data.frame)
    ##  $ price                   : num [1:10945] 530000 525000 480000 452000 365500 ...
    ##  $ date_sold               : Date[1:10945], format: "2016-01-13" "2016-01-13" ...
    ##  $ suburb                  : chr [1:10945] "Kincumber" "Halekulani" "Chittaway Bay" "Leumeah" ...
    ##  $ num_bath                : num [1:10945] 4 2 2 1 0 1 1 1 1 0 ...
    ##  $ num_bed                 : num [1:10945] 4 4 4 3 0 3 3 3 3 0 ...
    ##  $ num_parking             : num [1:10945] 2 2 2 1 0 1 1 2 3 0 ...
    ##  $ property_size           : num [1:10945] 1351 594 468 344 1850 ...
    ##  $ type                    : chr [1:10945] "House" "House" "House" "House" ...
    ##  $ suburb_population       : num [1:10945] 7093 2538 2028 9835 2200 ...
    ##  $ suburb_median_income    : num [1:10945] 29432 24752 31668 32292 45084 ...
    ##  $ suburb_sqkm             : num [1:10945] 9.91 1.4 1.12 4.05 1.5 ...
    ##  $ suburb_lat              : num [1:10945] -33.5 -33.2 -33.3 -34.1 -33.5 ...
    ##  $ suburb_lng              : num [1:10945] 151 152 151 151 151 ...
    ##  $ suburb_elevation        : num [1:10945] 24 23 3 81 18 24 27 81 4 263 ...
    ##  $ cash_rate               : num [1:10945] 2 2 2 2 2 2 2 2 2 2 ...
    ##  $ property_inflation_index: num [1:10945] 151 151 151 151 151 ...
    ##  $ km_from_cbd             : num [1:10945] 47 78.5 63.6 40.1 50 ...
    ##  $ year                    : chr [1:10945] "2016" "2016" "2016" "2016" ...

# Some general analysis

## Average property sold price by date_soldafter data cleaning

``` r
options(scipen = 999)
ggplot(cleaned_df, aes(x = date_sold, y= price)) + 
  geom_bar(stat = "summary", fun = "mean", fill="#56B4E9") +
  geom_smooth(method=lm)+
  labs(x = 'Time', y = 'Price', fill = 'type', title = 'Average price after cleaning')
```

    ## `geom_smooth()` using formula = 'y ~ x'

![](Sydney_property_sold_2016_2022_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->
## Average property price by year

``` r
options(scipen = 999)
ggplot(cleaned_df, aes(x = year, y=price)) + 
  geom_bar(stat = "summary", fun = "mean", fill="#56B4E9") +
  labs(x = 'Price', y = 'Year)', fill = 'type', title = 'Average price by year')
```

![](Sydney_property_sold_2016_2022_files/figure-gfm/unnamed-chunk-7-1.png)<!-- -->

## Average property price by year for different property types

``` r
options(scipen = 999)
ggplot(cleaned_df, aes(x = year, y= price)) + 
  geom_bar(stat = "summary", fun = "mean", fill="#56B4E9") +
  facet_wrap(~type)+
  labs(x = 'Year', y = 'Price)', fill = 'type', title = 'Average price by year')
```

![](Sydney_property_sold_2016_2022_files/figure-gfm/unnamed-chunk-8-1.png)<!-- -->

# Analyze 3 main housing types

## Create a vector of the four main types

``` r
main_types <- c("House", "Apartment / Unit / Flat", "Townhouse")
cleaned_df$type_grouped <- ifelse(cleaned_df$type %in% main_types, cleaned_df$type, "others")
print(cleaned_df)
```

    ## # A tibble: 10,945 × 19
    ##     price date_sold  suburb        num_b…¹ num_bed num_p…² prope…³ type  subur…⁴
    ##     <dbl> <date>     <chr>           <dbl>   <dbl>   <dbl>   <dbl> <chr>   <dbl>
    ##  1 530000 2016-01-13 Kincumber           4       4       2    1351 House    7093
    ##  2 525000 2016-01-13 Halekulani          2       4       2     594 House    2538
    ##  3 480000 2016-01-13 Chittaway Bay       2       4       2     468 House    2028
    ##  4 452000 2016-01-13 Leumeah             1       3       1     344 House    9835
    ##  5 365500 2016-01-13 North Avoca         0       0       0    1850 Vaca…    2200
    ##  6 550000 2016-01-15 Kincumber           1       3       1     626 House    7093
    ##  7 535000 2016-01-15 Bensville           1       3       1     556 House    2545
    ##  8 495000 2016-01-15 Leumeah             1       3       2     582 House    9835
    ##  9 410000 2016-01-15 Toukley             1       3       3     493 House    4550
    ## 10 242500 2016-01-15 Winmalee            0       0       0    1248 Vaca…    6202
    ## # … with 10,935 more rows, 10 more variables: suburb_median_income <dbl>,
    ## #   suburb_sqkm <dbl>, suburb_lat <dbl>, suburb_lng <dbl>,
    ## #   suburb_elevation <dbl>, cash_rate <dbl>, property_inflation_index <dbl>,
    ## #   km_from_cbd <dbl>, year <chr>, type_grouped <chr>, and abbreviated variable
    ## #   names ¹​num_bath, ²​num_parking, ³​property_size, ⁴​suburb_population

## Number of sold property by main types and other

``` r
options(scipen = 999)
ggplot(data=cleaned_df) +
  geom_bar(mapping=aes(x = type_grouped, fill=type_grouped))
```

![](Sydney_property_sold_2016_2022_files/figure-gfm/unnamed-chunk-10-1.png)<!-- -->

## Average property price by year for 3 main property types and other types

``` r
options(scipen = 999)
ggplot(cleaned_df, aes(x = year, y= price)) + 
  geom_bar(stat = "summary", fun = "mean", fill="#56B4E9") +
  facet_wrap(~type_grouped)+
  labs(x = 'Price', y = 'Year)', fill = 'type_grouped', title = 'Average price by year')
```

![](Sydney_property_sold_2016_2022_files/figure-gfm/unnamed-chunk-11-1.png)<!-- -->
## Price distribution by year

``` r
hist(cleaned_df$price, xlab = 'Price (AUD)', ylab = 'Number of sold', main = 'Distribution of House Prices from 2016-2022')
```

![](Sydney_property_sold_2016_2022_files/figure-gfm/unnamed-chunk-12-1.png)<!-- -->

## Price =by date of sold for 3 main property types and other types

``` r
options(scipen = 999)
ggplot(cleaned_df, aes(x = date_sold, y = price, alpha = date_sold))+
   geom_point(colour = 6) +
  facet_wrap(~type_grouped)+
  geom_smooth(method=lm)+
  labs(x = 'Time', y = 'Price', fill = 'type_grouped', title = 'Price by time')
```

    ## `geom_smooth()` using formula = 'y ~ x'

    ## Warning: The following aesthetics were dropped during statistical transformation: alpha
    ## ℹ This can happen when ggplot fails to infer the correct grouping structure in
    ##   the data.
    ## ℹ Did you forget to specify a `group` aesthetic or to convert a numerical
    ##   variable into a factor?
    ## The following aesthetics were dropped during statistical transformation: alpha
    ## ℹ This can happen when ggplot fails to infer the correct grouping structure in
    ##   the data.
    ## ℹ Did you forget to specify a `group` aesthetic or to convert a numerical
    ##   variable into a factor?
    ## The following aesthetics were dropped during statistical transformation: alpha
    ## ℹ This can happen when ggplot fails to infer the correct grouping structure in
    ##   the data.
    ## ℹ Did you forget to specify a `group` aesthetic or to convert a numerical
    ##   variable into a factor?
    ## The following aesthetics were dropped during statistical transformation: alpha
    ## ℹ This can happen when ggplot fails to infer the correct grouping structure in
    ##   the data.
    ## ℹ Did you forget to specify a `group` aesthetic or to convert a numerical
    ##   variable into a factor?

![](Sydney_property_sold_2016_2022_files/figure-gfm/unnamed-chunk-13-1.png)<!-- -->
## Price distribution by property types

``` r
ggplot(cleaned_df, aes(x = price)) +
  geom_histogram(aes(color = type_grouped, fill = type_grouped), 
                bins = 30, alpha = 0.4)
```

![](Sydney_property_sold_2016_2022_files/figure-gfm/unnamed-chunk-14-1.png)<!-- -->
# Analyze pricer per property size (m2) ## Create new “price_per_size”
column

``` r
cleaned_df$price_per_size <- cleaned_df$price/cleaned_df$property_size
summary(cleaned_df$price_per_size)
```

    ##      Min.   1st Qu.    Median      Mean   3rd Qu.      Max. 
    ##     16.16   1505.81   2341.95   3631.99   4006.02 175000.00

## Price per size by year for different property types

``` r
options(scipen = 999)
ggplot(cleaned_df, aes(x = year, y= price_per_size)) + 
  geom_bar(stat = "summary", fun = "mean", fill="#56B4E9") +
  facet_wrap(~type_grouped)+
  labs(x = 'Price per size', y = 'Year)', fill = 'type_grouped', title = 'Average price per housing size by year')
```

![](Sydney_property_sold_2016_2022_files/figure-gfm/unnamed-chunk-16-1.png)<!-- -->
## Test for correlation between price and other property features

``` r
price_vs_size <- cor.test(cleaned_df$price, cleaned_df$property_size, 
                    method = "pearson")
price_vs_size
```

    ## 
    ##  Pearson's product-moment correlation
    ## 
    ## data:  cleaned_df$price and cleaned_df$property_size
    ## t = 9.5119, df = 10943, p-value < 0.00000000000000022
    ## alternative hypothesis: true correlation is not equal to 0
    ## 95 percent confidence interval:
    ##  0.07194161 0.10910405
    ## sample estimates:
    ##        cor 
    ## 0.09055435

``` r
price_vs_distance <- cor.test(cleaned_df$price, cleaned_df$km_from_cbd, 
                    method = "pearson")
price_vs_distance
```

    ## 
    ##  Pearson's product-moment correlation
    ## 
    ## data:  cleaned_df$price and cleaned_df$km_from_cbd
    ## t = -52.544, df = 10943, p-value < 0.00000000000000022
    ## alternative hypothesis: true correlation is not equal to 0
    ## 95 percent confidence interval:
    ##  -0.4636891 -0.4337663
    ## sample estimates:
    ##        cor 
    ## -0.4488535

``` r
price_vs_population <- cor.test(cleaned_df$price, cleaned_df$suburb_population, 
                    method = "pearson")
price_vs_population
```

    ## 
    ##  Pearson's product-moment correlation
    ## 
    ## data:  cleaned_df$price and cleaned_df$suburb_population
    ## t = -4.3255, df = 10943, p-value = 0.00001535
    ## alternative hypothesis: true correlation is not equal to 0
    ## 95 percent confidence interval:
    ##  -0.06000277 -0.02259712
    ## sample estimates:
    ##         cor 
    ## -0.04131442

``` r
price_vs_income <- cor.test(cleaned_df$price, cleaned_df$suburb_median_income, 
                    method = "pearson")
price_vs_income
```

    ## 
    ##  Pearson's product-moment correlation
    ## 
    ## data:  cleaned_df$price and cleaned_df$suburb_median_income
    ## t = 44.727, df = 10943, p-value < 0.00000000000000022
    ## alternative hypothesis: true correlation is not equal to 0
    ## 95 percent confidence interval:
    ##  0.3771810 0.4088612
    ## sample estimates:
    ##       cor 
    ## 0.3931378

``` r
price_vs_elevation <- cor.test(cleaned_df$price, cleaned_df$suburb_elevation, 
                    method = "pearson")
price_vs_elevation 
```

    ## 
    ##  Pearson's product-moment correlation
    ## 
    ## data:  cleaned_df$price and cleaned_df$suburb_elevation
    ## t = 1.54, df = 10943, p-value = 0.1236
    ## alternative hypothesis: true correlation is not equal to 0
    ## 95 percent confidence interval:
    ##  -0.004015714  0.033445757
    ## sample estimates:
    ##        cor 
    ## 0.01472019

# Save cleaned data to a new file

``` r
cleaned_df %>%
  write.csv("domain_properties_clean.csv")
```
