---
title: "Stock Data"
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



## DOW

The Following table was made


::: {.cell}

```{.r .cell-code}
library(tidyverse)
library(readr)
library(readxl)
library(stringr)
library(gt)

Dow <- read_excel("C:/Users/seanw/Downloads/Dart_Expert_Dow_6month_anova.xlsx")

#data <- separate(data, combined, into = c("fruit1", "fruit2"), sep = "_")

Dow_2 <- Dow %>%
  separate(contest_period, into = c("start","end"), sep = "-")

Dow_3 <- Dow_2 %>%
  mutate(end_month = substr(end, 1, nchar(end) - 4), 
         end_year = substr(end, nchar(end) - 3, nchar(end)))  %>%
  filter(variable == "DJIA")
Dow_4 <- Dow_3 %>%
  select(end_month,
         end_year,
         value)
Dow_5 <- Dow_4 %>%
  pivot_wider(
    names_from = end_year, 
    values_from = value
  )
gt(Dow_5)
```

::: {.cell-output-display}


```{=html}
<div id="ibeeyvemyn" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#ibeeyvemyn table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#ibeeyvemyn thead, #ibeeyvemyn tbody, #ibeeyvemyn tfoot, #ibeeyvemyn tr, #ibeeyvemyn td, #ibeeyvemyn th {
  border-style: none;
}

#ibeeyvemyn p {
  margin: 0;
  padding: 0;
}

#ibeeyvemyn .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#ibeeyvemyn .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}

#ibeeyvemyn .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#ibeeyvemyn .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#ibeeyvemyn .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#ibeeyvemyn .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#ibeeyvemyn .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#ibeeyvemyn .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#ibeeyvemyn .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#ibeeyvemyn .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#ibeeyvemyn .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#ibeeyvemyn .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#ibeeyvemyn .gt_spanner_row {
  border-bottom-style: hidden;
}

#ibeeyvemyn .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}

#ibeeyvemyn .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#ibeeyvemyn .gt_from_md > :first-child {
  margin-top: 0;
}

#ibeeyvemyn .gt_from_md > :last-child {
  margin-bottom: 0;
}

#ibeeyvemyn .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#ibeeyvemyn .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}

#ibeeyvemyn .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}

#ibeeyvemyn .gt_row_group_first td {
  border-top-width: 2px;
}

#ibeeyvemyn .gt_row_group_first th {
  border-top-width: 2px;
}

#ibeeyvemyn .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#ibeeyvemyn .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#ibeeyvemyn .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#ibeeyvemyn .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#ibeeyvemyn .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#ibeeyvemyn .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#ibeeyvemyn .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}

#ibeeyvemyn .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#ibeeyvemyn .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#ibeeyvemyn .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#ibeeyvemyn .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#ibeeyvemyn .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#ibeeyvemyn .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#ibeeyvemyn .gt_left {
  text-align: left;
}

#ibeeyvemyn .gt_center {
  text-align: center;
}

#ibeeyvemyn .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#ibeeyvemyn .gt_font_normal {
  font-weight: normal;
}

#ibeeyvemyn .gt_font_bold {
  font-weight: bold;
}

#ibeeyvemyn .gt_font_italic {
  font-style: italic;
}

#ibeeyvemyn .gt_super {
  font-size: 65%;
}

#ibeeyvemyn .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}

#ibeeyvemyn .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#ibeeyvemyn .gt_indent_1 {
  text-indent: 5px;
}

#ibeeyvemyn .gt_indent_2 {
  text-indent: 10px;
}

#ibeeyvemyn .gt_indent_3 {
  text-indent: 15px;
}

#ibeeyvemyn .gt_indent_4 {
  text-indent: 20px;
}

#ibeeyvemyn .gt_indent_5 {
  text-indent: 25px;
}

#ibeeyvemyn .katex-display {
  display: inline-flex !important;
  margin-bottom: 0.75em !important;
}

#ibeeyvemyn div.Reactable > div.rt-table > div.rt-thead > div.rt-tr.rt-tr-group-header > div.rt-th-group:after {
  height: 0px !important;
}
</style>
<table class="gt_table" data-quarto-disable-processing="false" data-quarto-bootstrap="false">
  <thead>
    <tr class="gt_col_headings">
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="end_month">end_month</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col" id="a1990">1990</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col" id="a1991">1991</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col" id="a1992">1992</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col" id="a1993">1993</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col" id="a1994">1994</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col" id="a1995">1995</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col" id="a1996">1996</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col" id="a1997">1997</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col" id="a1998">1998</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="end_month" class="gt_row gt_left">June</td>
<td headers="1990" class="gt_row gt_right">2.5</td>
<td headers="1991" class="gt_row gt_right">17.7</td>
<td headers="1992" class="gt_row gt_right">3.6</td>
<td headers="1993" class="gt_row gt_right">7.7</td>
<td headers="1994" class="gt_row gt_right">-6.2</td>
<td headers="1995" class="gt_row gt_right">16.0</td>
<td headers="1996" class="gt_row gt_right">10.2</td>
<td headers="1997" class="gt_row gt_right">16.2</td>
<td headers="1998" class="gt_row gt_right">15.0</td></tr>
    <tr><td headers="end_month" class="gt_row gt_left">July</td>
<td headers="1990" class="gt_row gt_right">11.5</td>
<td headers="1991" class="gt_row gt_right">7.6</td>
<td headers="1992" class="gt_row gt_right">4.2</td>
<td headers="1993" class="gt_row gt_right">3.7</td>
<td headers="1994" class="gt_row gt_right">-5.3</td>
<td headers="1995" class="gt_row gt_right">19.6</td>
<td headers="1996" class="gt_row gt_right">1.3</td>
<td headers="1997" class="gt_row gt_right">20.8</td>
<td headers="1998" class="gt_row gt_right">7.1</td></tr>
    <tr><td headers="end_month" class="gt_row gt_left">August</td>
<td headers="1990" class="gt_row gt_right">-2.3</td>
<td headers="1991" class="gt_row gt_right">4.4</td>
<td headers="1992" class="gt_row gt_right">-0.3</td>
<td headers="1993" class="gt_row gt_right">7.3</td>
<td headers="1994" class="gt_row gt_right">1.5</td>
<td headers="1995" class="gt_row gt_right">15.3</td>
<td headers="1996" class="gt_row gt_right">0.6</td>
<td headers="1997" class="gt_row gt_right">8.3</td>
<td headers="1998" class="gt_row gt_right">-13.1</td></tr>
    <tr><td headers="end_month" class="gt_row gt_left">September</td>
<td headers="1990" class="gt_row gt_right">-9.2</td>
<td headers="1991" class="gt_row gt_right">3.4</td>
<td headers="1992" class="gt_row gt_right">-0.1</td>
<td headers="1993" class="gt_row gt_right">5.2</td>
<td headers="1994" class="gt_row gt_right">4.4</td>
<td headers="1995" class="gt_row gt_right">14.0</td>
<td headers="1996" class="gt_row gt_right">5.8</td>
<td headers="1997" class="gt_row gt_right">20.2</td>
<td headers="1998" class="gt_row gt_right">-11.8</td></tr>
    <tr><td headers="end_month" class="gt_row gt_left">October</td>
<td headers="1990" class="gt_row gt_right">-8.5</td>
<td headers="1991" class="gt_row gt_right">4.4</td>
<td headers="1992" class="gt_row gt_right">-5.0</td>
<td headers="1993" class="gt_row gt_right">5.7</td>
<td headers="1994" class="gt_row gt_right">6.9</td>
<td headers="1995" class="gt_row gt_right">8.2</td>
<td headers="1996" class="gt_row gt_right">7.2</td>
<td headers="1997" class="gt_row gt_right">3.0</td>
<td headers="1998" class="gt_row gt_right">NA</td></tr>
    <tr><td headers="end_month" class="gt_row gt_left">November</td>
<td headers="1990" class="gt_row gt_right">-12.8</td>
<td headers="1991" class="gt_row gt_right">-3.3</td>
<td headers="1992" class="gt_row gt_right">-2.8</td>
<td headers="1993" class="gt_row gt_right">4.9</td>
<td headers="1994" class="gt_row gt_right">-0.3</td>
<td headers="1995" class="gt_row gt_right">13.1</td>
<td headers="1996" class="gt_row gt_right">15.1</td>
<td headers="1997" class="gt_row gt_right">3.8</td>
<td headers="1998" class="gt_row gt_right">NA</td></tr>
    <tr><td headers="end_month" class="gt_row gt_left">December</td>
<td headers="1990" class="gt_row gt_right">-9.3</td>
<td headers="1991" class="gt_row gt_right">6.6</td>
<td headers="1992" class="gt_row gt_right">0.2</td>
<td headers="1993" class="gt_row gt_right">NA</td>
<td headers="1994" class="gt_row gt_right">3.6</td>
<td headers="1995" class="gt_row gt_right">9.3</td>
<td headers="1996" class="gt_row gt_right">15.5</td>
<td headers="1997" class="gt_row gt_right">-0.7</td>
<td headers="1998" class="gt_row gt_right">NA</td></tr>
    <tr><td headers="end_month" class="gt_row gt_left">January</td>
<td headers="1990" class="gt_row gt_right">NA</td>
<td headers="1991" class="gt_row gt_right">-0.8</td>
<td headers="1992" class="gt_row gt_right">6.5</td>
<td headers="1993" class="gt_row gt_right">-0.8</td>
<td headers="1994" class="gt_row gt_right">11.2</td>
<td headers="1995" class="gt_row gt_right">1.8</td>
<td headers="1996" class="gt_row gt_right">15.0</td>
<td headers="1997" class="gt_row gt_right">19.6</td>
<td headers="1998" class="gt_row gt_right">-0.3</td></tr>
    <tr><td headers="end_month" class="gt_row gt_left">February</td>
<td headers="1990" class="gt_row gt_right">NA</td>
<td headers="1991" class="gt_row gt_right">11.0</td>
<td headers="1992" class="gt_row gt_right">8.6</td>
<td headers="1993" class="gt_row gt_right">2.5</td>
<td headers="1994" class="gt_row gt_right">5.5</td>
<td headers="1995" class="gt_row gt_right">NA</td>
<td headers="1996" class="gt_row gt_right">15.6</td>
<td headers="1997" class="gt_row gt_right">20.1</td>
<td headers="1998" class="gt_row gt_right">10.7</td></tr>
    <tr><td headers="end_month" class="gt_row gt_left">March</td>
<td headers="1990" class="gt_row gt_right">NA</td>
<td headers="1991" class="gt_row gt_right">15.8</td>
<td headers="1992" class="gt_row gt_right">7.2</td>
<td headers="1993" class="gt_row gt_right">9.0</td>
<td headers="1994" class="gt_row gt_right">1.6</td>
<td headers="1995" class="gt_row gt_right">7.3</td>
<td headers="1996" class="gt_row gt_right">18.4</td>
<td headers="1997" class="gt_row gt_right">9.6</td>
<td headers="1998" class="gt_row gt_right">7.6</td></tr>
    <tr><td headers="end_month" class="gt_row gt_left">April</td>
<td headers="1990" class="gt_row gt_right">NA</td>
<td headers="1991" class="gt_row gt_right">16.2</td>
<td headers="1992" class="gt_row gt_right">10.6</td>
<td headers="1993" class="gt_row gt_right">5.8</td>
<td headers="1994" class="gt_row gt_right">0.5</td>
<td headers="1995" class="gt_row gt_right">12.8</td>
<td headers="1996" class="gt_row gt_right">14.8</td>
<td headers="1997" class="gt_row gt_right">15.3</td>
<td headers="1998" class="gt_row gt_right">22.5</td></tr>
    <tr><td headers="end_month" class="gt_row gt_left">May</td>
<td headers="1990" class="gt_row gt_right">NA</td>
<td headers="1991" class="gt_row gt_right">17.3</td>
<td headers="1992" class="gt_row gt_right">17.6</td>
<td headers="1993" class="gt_row gt_right">6.7</td>
<td headers="1994" class="gt_row gt_right">1.3</td>
<td headers="1995" class="gt_row gt_right">19.5</td>
<td headers="1996" class="gt_row gt_right">9.0</td>
<td headers="1997" class="gt_row gt_right">13.3</td>
<td headers="1998" class="gt_row gt_right">10.6</td></tr>
    <tr><td headers="end_month" class="gt_row gt_left">Dec.</td>
<td headers="1990" class="gt_row gt_right">NA</td>
<td headers="1991" class="gt_row gt_right">NA</td>
<td headers="1992" class="gt_row gt_right">NA</td>
<td headers="1993" class="gt_row gt_right">8.0</td>
<td headers="1994" class="gt_row gt_right">NA</td>
<td headers="1995" class="gt_row gt_right">NA</td>
<td headers="1996" class="gt_row gt_right">NA</td>
<td headers="1997" class="gt_row gt_right">NA</td>
<td headers="1998" class="gt_row gt_right">NA</td></tr>
    <tr><td headers="end_month" class="gt_row gt_left">Febuary</td>
<td headers="1990" class="gt_row gt_right">NA</td>
<td headers="1991" class="gt_row gt_right">NA</td>
<td headers="1992" class="gt_row gt_right">NA</td>
<td headers="1993" class="gt_row gt_right">NA</td>
<td headers="1994" class="gt_row gt_right">NA</td>
<td headers="1995" class="gt_row gt_right">3.2</td>
<td headers="1996" class="gt_row gt_right">NA</td>
<td headers="1997" class="gt_row gt_right">NA</td>
<td headers="1998" class="gt_row gt_right">NA</td></tr>
  </tbody>
  
  
</table>
</div>
```


:::
:::
