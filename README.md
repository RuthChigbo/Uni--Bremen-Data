# Uni--Bremen-Data
Analysis the University Metrological data using R
---
title: "Untitled"
output: html_document
date: "2022-08-25"
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```


```{r}
library(data.table)
library(dplyr)
library(readr)
library(tidyr)
library(ggplot2)
library(forcats)
library(ggridges)
library(viridis)

```
#selecting the necessary column
```{r}
bind_rows(F, FF, RAD, N, SD, T2M, RR) %>%
ggplot(aes(Zeitstempel, Wert, color = "Produkt_Code")) +
  geom_line() +
  geom_point()+
  geom_ridgeline(fill = "lightbluE")

bind_rows(F, FF, RAD, N, SD, T2M, RR) %>%
ggplot(aes(Zeitstempel, Wert, group = Wert)) +
  geom_density()+
 facet_grid(rows = vars(Produkt_Code))



bind_rows(F, FF, RAD, N, SD, T2M, RR) %>%
ggplot(aes(Zeitstempel, Wert, height = Wert, group = Wert)) +
  geom_ridgeline(fill = "red")+
 facet_grid(rows = vars(Produkt_Code))




bind_rows(F, FF, RAD, N, SD, T2M, RR) %>%
ggplot(aes(Zeitstempel, Wert, height = Wert, group = Wert)) +
  geom_density_ridges2()+
 facet_grid(rows = vars(Produkt_Code))
```

 # Draw histogram
```{r}
histogram <-                                        
 bind_rows(F, FF, RAD, N, SD, T2M, RR) %>%
  ggplot(aes(x = Zeitstempel, fill = Wert) +
  geom_histogram() 
histogram
```

# Draw facet plot
```{r}
faceted_histogram <-                                 
  histogram +
  facet_wrap(~ Wert, nrow = 4)
faceted_histogram
```

# Draw histograms in ridgeline plot
```{r}
ridge_histogram_plot <-                              
  bind_rows(F, FF, RAD, N, SD, T2M, RR) %>%
  ggplot(aes(x = Zeitstempel, y = Wert,  fill = Wert)) +
  geom_density_ridges(scale = 1,
                                stat = "binline")
ridge_histogram_plot
```

```{r}
F <- 
  read_csv("Data/data_OBS_DEU_PT1H_F.csv") %>% 
  select(Zeitstempel, Produkt_Code, Wert)

FF <- 
  read_csv("Data/data_OBS_DEU_PT1H_FF.csv") %>% 
  select(Zeitstempel, Produkt_Code, Wert)

N <- 
  read_csv("Data/data_OBS_DEU_PT1H_N.csv") %>% 
  select(Zeitstempel, Produkt_Code, Wert)

data_OBS_DEU_PT1H_RF <- 
  read_csv("Data/data_OBS_DEU_PT1H_RF.csv") %>% 
  select(Zeitstempel, Produkt_Code, Wert)

SD <- 
  read_csv("Data/data_OBS_DEU_PT1H_SD.csv") %>% 
  select(Zeitstempel, Produkt_Code, Wert)

RR <- 
  read_csv("Data/data_OBS_DEU_PT1H_RR.csv") %>% 
  select(Zeitstempel, Produkt_Code, Wert)

T2M <- 
  read_csv("Data/data_OBS_DEU_PT1H_T2M.csv") %>% 
  select(Zeitstempel, Produkt_Code, Wert)

RAD <- 
  read_csv("Data/data_OBS_DEU_PT10M_RAD-G.csv") %>% 
  select(Zeitstempel, Produkt_Code, Wert)
```
#converting  time stamp to date time
```{r}
 gen.all <- (my.cloud.list$`1`, my.gr.list$`1`, my.ppt.list$`1`, my.rh.list$`1`, my.sun.list$`1`, my.tp.list$`1`, my.wd.list$`1`)
 select(Zeitstempel, Produkt_Code, Wert)
```


```{r}
meta.gen <- bind_rows(F, FF, RAD, N, SD, T2M, RR) 
  gen.all <- bind_rows(my.cloud.list$`1`, my.gr.list$`1`, my.ppt.list$`1`, my.rh.list$`1`, my.sun.list$`1`, my.tp.list$`1`, my.wd.list$`1`)
```

#ploting all the data
```{r}
bind_rows(F, FF, RAD, N, SD, T2M, RR) %>%
ggplot(aes(Zeitstempel, Wert, color = "Produkt_Code")) +
  geom_line() +
  geom_point()+
facet_grid(rows = vars(Produkt_Code))

```


