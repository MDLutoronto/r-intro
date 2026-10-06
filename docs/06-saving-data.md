---
title: New Variables
layout: home
staff:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
maintainer:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
created_date: 2016-08-17
nav_order: 6
parent: Introduction to R
---
## Saving Data

### Saving R object

**saveRDS()** can be used to save a dataset as a native R .rds data file.

```
# Saving R Object
saveRDS(cchs, file = "cchs_analysis.rds")
```

### Exporting data as CSV

**write.csv()** can be used to export a dataset as a CSV file. The `row.names` argument allows us to choose whether to export the data row numbers as a column or not. In this example, we set it to `FALSE` in order to avoid having an extra column with the row number in the exported file.

```
# Exporting Data as CSV
write.csv(cchs, file = "cchs_analysis.csv", row.names = FALSE)
```

**Technique:** [Converting data formats](https://mdlutoronto.github.io/tutorials-search/?technique=Converting+data+formats), [Cleaning data](https://mdlutoronto.github.io/tutorials-search/?technique=Cleaning+data), [Extracting data](https://mdlutoronto.github.io/tutorials-search/?technique=Extracting+data)\
**Tools:** [R](https://mdlutoronto.github.io/tutorials-search/?tool=R)\
**Data Format:** [Statistics](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Statistics)