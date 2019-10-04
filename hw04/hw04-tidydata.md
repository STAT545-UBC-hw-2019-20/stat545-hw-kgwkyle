---
title: 'Assignment 4: Tidy Data'
author: "Kyle Wlodarczyk"
date: "October 4, 2019"
output: 
  html_document:
    keep_md: true
    df_print: paged
    toc: yes
    theme: cerulean
---

Before we begin, let us load some packages that we will potentially be using. 


```r
library(tidyverse)
library(gapminder)
library(tibble)
library(DT)
```

# Exercise 1 - Univariate Option 1

Let's take a look at the life expectancy of two countries, such as Poland and Switzerland, for each year. Note that in the table below, the values have been rounded and are given in the unit "years".


```r
gapminder_r = gapminder
gapminder_r$lifeExp = round(gapminder_r$lifeExp, 1)

Ex1 <- gapminder_r %>%
  select(country, year, lifeExp) %>%
  filter(country == "Poland" | country == "Switzerland") %>%
  pivot_wider(id_cols = year,
              names_from = country,
              values_from = lifeExp)

datatable(Ex1)
```

<!--html_preserve--><div id="htmlwidget-1709f129138fe1786849" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-1709f129138fe1786849">{"x":{"filter":"none","data":[["1","2","3","4","5","6","7","8","9","10","11","12"],[1952,1957,1962,1967,1972,1977,1982,1987,1992,1997,2002,2007],[61.3,65.8,67.6,69.6,70.8,70.7,71.3,71,71,72.8,74.7,75.6],[69.6,70.6,71.3,72.8,73.8,75.4,76.2,77.4,78,79.4,80.6,81.7]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>year<\/th>\n      <th>Poland<\/th>\n      <th>Switzerland<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"columnDefs":[{"className":"dt-right","targets":[1,2,3]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false}},"evals":[],"jsHooks":[]}</script><!--/html_preserve-->

To get a better idea of how the life expectancies of the two countries are changing relative to each other, let's graph them against each other since visuals are powerful communication tools.


```r
Ex1 %>%
  ggplot() +
  geom_point(aes(Poland, Switzerland)) +
  xlab("Poland") +
  ylab("Switzerland") +
  ggtitle("Life Expectancy in Poland and Switzerland") +
  geom_text(aes(Poland, Switzerland, label = year), hjust = .1, vjust = -.3) +
  theme_bw()
```

![](hw04-tidydata_files/figure-html/unnamed-chunk-3-1.png)<!-- -->

We can see that the life expectancy in Poland stagnates between 1972 and 1992 while it continues to increase in Switzerland.

Now let's return the data back to the format found in the gapminder dataset, where observations are listed for each country and arranged by country followed by year.


```r
Ex1 %>%
  pivot_longer(cols = c(Poland, Switzerland),
               names_to = "country",
               values_to = "lifeExp") %>%
  select(country, year, lifeExp) %>%
  arrange(country) %>%
  datatable()
```

<!--html_preserve--><div id="htmlwidget-a1014602cc2407c7d3a6" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-a1014602cc2407c7d3a6">{"x":{"filter":"none","data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24"],["Poland","Poland","Poland","Poland","Poland","Poland","Poland","Poland","Poland","Poland","Poland","Poland","Switzerland","Switzerland","Switzerland","Switzerland","Switzerland","Switzerland","Switzerland","Switzerland","Switzerland","Switzerland","Switzerland","Switzerland"],[1952,1957,1962,1967,1972,1977,1982,1987,1992,1997,2002,2007,1952,1957,1962,1967,1972,1977,1982,1987,1992,1997,2002,2007],[61.3,65.8,67.6,69.6,70.8,70.7,71.3,71,71,72.8,74.7,75.6,69.6,70.6,71.3,72.8,73.8,75.4,76.2,77.4,78,79.4,80.6,81.7]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>country<\/th>\n      <th>year<\/th>\n      <th>lifeExp<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"columnDefs":[{"className":"dt-right","targets":[2,3]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false}},"evals":[],"jsHooks":[]}</script><!--/html_preserve-->


# Exercise 2 - Multivariate Option 1

After reviewing the life expectancy of Poland and Switzerland for each year, let's see how the GDP per capita changes with life expectancy. Note that in the table below, the values have been rounded and are given in the unit "years" for life expectancy or "dollars" for GDP per capita.


```r
gapminder_r$gdpPercap = round(gapminder_r$gdpPercap, 2)

Ex2 <- gapminder_r %>%
  select(country, year, lifeExp, gdpPercap) %>%
  filter(country == "Poland" | country == "Switzerland") %>%
  pivot_wider(id_cols = year,
              names_from = country,
              values_from = c(lifeExp, gdpPercap)) %>%
  select(year, lifeExp_Poland, gdpPercap_Poland, lifeExp_Switzerland, gdpPercap_Switzerland)

datatable(Ex2)
```

<!--html_preserve--><div id="htmlwidget-af17daf52f8a35d00de6" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-af17daf52f8a35d00de6">{"x":{"filter":"none","data":[["1","2","3","4","5","6","7","8","9","10","11","12"],[1952,1957,1962,1967,1972,1977,1982,1987,1992,1997,2002,2007],[61.3,65.8,67.6,69.6,70.8,70.7,71.3,71,71,72.8,74.7,75.6],[4029.33,4734.25,5338.75,6557.15,8006.51,9508.14,8451.53,9082.35,7738.88,10159.58,12002.24,15389.92],[69.6,70.6,71.3,72.8,73.8,75.4,76.2,77.4,78,79.4,80.6,81.7],[14734.23,17909.49,20431.09,22966.14,27195.11,26982.29,28397.72,30281.7,31871.53,32135.32,34480.96,37506.42]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>year<\/th>\n      <th>lifeExp_Poland<\/th>\n      <th>gdpPercap_Poland<\/th>\n      <th>lifeExp_Switzerland<\/th>\n      <th>gdpPercap_Switzerland<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"columnDefs":[{"className":"dt-right","targets":[1,2,3,4,5]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false}},"evals":[],"jsHooks":[]}</script><!--/html_preserve-->

Now that we've seen how GDP per capita compares to life expectancy for both Poland and Switzerland, let's return the data back to the format found in the gapminder dataset, where observations are listed for each country and arranged by country followed by year.


```r
Ex2 %>%
  pivot_longer(cols      = -year, 
               names_to  = c(".value", "country"),
               names_sep = "_") %>%
  select(country, year, lifeExp, gdpPercap) %>%
  arrange(country) %>%
  datatable()
```

<!--html_preserve--><div id="htmlwidget-24ae1f084c8e90ca7384" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-24ae1f084c8e90ca7384">{"x":{"filter":"none","data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24"],["Poland","Poland","Poland","Poland","Poland","Poland","Poland","Poland","Poland","Poland","Poland","Poland","Switzerland","Switzerland","Switzerland","Switzerland","Switzerland","Switzerland","Switzerland","Switzerland","Switzerland","Switzerland","Switzerland","Switzerland"],[1952,1957,1962,1967,1972,1977,1982,1987,1992,1997,2002,2007,1952,1957,1962,1967,1972,1977,1982,1987,1992,1997,2002,2007],[61.3,65.8,67.6,69.6,70.8,70.7,71.3,71,71,72.8,74.7,75.6,69.6,70.6,71.3,72.8,73.8,75.4,76.2,77.4,78,79.4,80.6,81.7],[4029.33,4734.25,5338.75,6557.15,8006.51,9508.14,8451.53,9082.35,7738.88,10159.58,12002.24,15389.92,14734.23,17909.49,20431.09,22966.14,27195.11,26982.29,28397.72,30281.7,31871.53,32135.32,34480.96,37506.42]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>country<\/th>\n      <th>year<\/th>\n      <th>lifeExp<\/th>\n      <th>gdpPercap<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"columnDefs":[{"className":"dt-right","targets":[2,3,4]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false}},"evals":[],"jsHooks":[]}</script><!--/html_preserve-->


#Exercise 3



