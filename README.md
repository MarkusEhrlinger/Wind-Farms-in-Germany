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

```



For NRW (North-Rhine-Westphalia) the coordinates were in a link, so I took the url of this link to get the coordinates.


```R
nrw_link = "https://de.wikipedia.org/wiki/Liste_von_Windkraftanlagen_in_Nordrhein-Westfalen"
nrw_page = read_html(nrw_link)

nrw_table = nrw_page %>% html_nodes("table") %>% .[1] %>%
  html_table() %>% .[[1]]

koordinaten = nrw_page %>%
  html_nodes("table") %>% .[1] %>%
    html_elements("a.external.text") %>% html_attr("href")

```

-----------------------------------------------------------------------------------

Then put everythin into a CSV-file example:

```R
 ger_table <- rbind(ger_table, bb_table[,1:10]) #combine tables

 colnames(bb_table) = colnames(ger_table) #adjust table to reference

 write_csv(ger_table, "ger_table.csv")

 ```

------------------------------------------------------------------------------------

Data was messy, I cleaned it in Google Sheets.
Main focus was to get the coordinates in a format accepted by Tableau.

From this...

![Raw-Latitude](https://github.com/MarkusEhrlinger/Wind-Farms-in-Germany/assets/132265260/73bc4609-a132-4ef8-b625-da7b73f98344)


To this...

![Clean-Latitude](https://github.com/MarkusEhrlinger/Wind-Farms-in-Germany/assets/132265260/dfec41c8-b608-4eaa-9b42-c8b950647459)


----------------------------------------------------------------------------------

This is the result in Tableau

https://public.tableau.com/views/Windparks-Deutschland/Sheet1?:language=de-DE&:display_count=n&:origin=viz_share_link

![Tableau-Map](https://github.com/MarkusEhrlinger/Wind-Farms-in-Germany/assets/132265260/05cbfd8a-43ea-4632-8af5-3fabdf486c88)

-----------------------------------------------------------------------------------

I still need to work on the filters, especially manufacturers.







  

