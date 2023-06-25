# Wind-Farms-in-Germany
A fun project, put the wind farms in Germany on a map.

I want to create a map of wind farms in Germany.

I took the data from Wikipedia.
https://de.wikipedia.org/wiki/Liste_von_Windkraftanlagen_in_Deutschland



***Data Gathering***

I scrapped the data from every list.
Repeated it for each single list. 

Here example code in R for Bavaria 

```R
library (rvest)
library (dplyr)

by_link = "https://de.wikipedia.org/wiki/Liste_von_Windkraftanlagen_in_Bayern"
by_page = read_html(by_link)

by_table = by_page %>% html_nodes("table") %>% .[1] %>%
  html_table() %>% .[[1]]

```R


__________________________________________________________________________________________________________

For NRW (North-Rhine-Westphalia) the coordinates were in a link, so I took the url of this link to get the coordinates.


```R
nrw_link = "https://de.wikipedia.org/wiki/Liste_von_Windkraftanlagen_in_Nordrhein-Westfalen"
nrw_page = read_html(nrw_link)

nrw_table = nrw_page %>% html_nodes("table") %>% .[1] %>%
  html_table() %>% .[[1]]

koordinaten = nrw_page %>%
  html_nodes("table") %>% .[1] %>%
    html_elements("a.external.text") %>% html_attr("href")

´´´R

-----------------------------------------------------------------------------------



  

