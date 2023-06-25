# Wind-Farms-in-Germany
A fun project, put the wind farms in Germany on a map.

I want to create a map of wind farms in Germany.\n

I took the data from Wikipedia.\n
https://de.wikipedia.org/wiki/Liste_von_Windkraftanlagen_in_Deutschland \n

I scrapped the data from every list.\n
Repeated it for each single list. 

Here example for Bavaria
´´´r
library (rvest)
library (dplyr)

by_link = "https://de.wikipedia.org/wiki/Liste_von_Windkraftanlagen_in_Bayern"
by_page = read_html(by_link)

by_table = by_page %>% html_nodes("table") %>% .[1] %>%
  html_table() %>% .[[1]]
´´´


  

