---
title: "Gapminder part 2"
author: "Sean Ramos"
editor: visual
execute:
  keep-md: true
  warning: false
format:
  html:
    code-fold: true
    code-tools: true
---


::: {.cell}

```{.r .cell-code}
library(tidyverse)
library(gapminder)

# Calculate weighted mean GDP per capita for each continent and year
gapminder_w <- gapminder %>%
  filter(country != "Kuwait") %>%
  group_by(continent, year) %>%
  summarize(wmgdp = weighted.mean(gdpPercap),
            wmpop = weighted.mean(pop),
            .groups = 'drop')


gapminder_c <- gapminder %>%
  filter(country != "Kuwait")



# plot
ggplot() +
  
  geom_line(data = gapminder_c, aes(x = year, y = gdpPercap, group = country, color = continent), alpha = 0.4) + 
  
  geom_point(data = gapminder_c, aes(x = year, y = gdpPercap, size = pop, colour = continent)) +
  
   geom_line(data = gapminder_w, aes(x = year, y = wmgdp), size = 1)+
  
  geom_point(data = gapminder_w, aes(x = year, y = wmgdp, size = wmpop)) +
  
  facet_wrap(~continent, nrow = 1)+
  theme_bw()+
  scale_size_continuous(
    name = "Population (100K)",  
    labels = scales::label_number(scale = 1e-5, accuracy = 0.1)  
  ) +
    guides(
    size = guide_legend(title = "Population (100K)"),  
    color = guide_legend(title = "Continent")  
  )+
  labs(title = "GDP Growth Across The World", x = "years", y = "GDP Per Capita")
```

::: {.cell-output-display}
![](jan21gdpgrowthacrosstheworld_files/figure-html/unnamed-chunk-1-1.png){width=672}
:::
:::
