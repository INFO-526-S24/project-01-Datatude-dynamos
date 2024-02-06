# Data
-   **[Dataset: refugees]**: Our target dataset comes from the {refugees} R package, which compiles extensive information on populations that have been strongly displaced from three main sources: UNHCR, UNRWA, and IDMC. Including refugees, asylum seekers, internally displaced people (IDPs), stateless people, and other groups of concern, this dataset covers a wide range of displacement categories from 2010 to 2022. The dataset has thorough information on each record categorized by the year of data collection, as well as quantitative metrics on various displaced population groups and the countries of origin and asylum (with the corresponding UNHCR and ISO codes). At 64,809 rows, this dataset is large and provides a detailed look at changes in displacement over a period of more than ten years. It is an invaluable tool for studying worldwide migration patterns.


# Codebook for [refugees] Dataset
```{r}
# Option 1: tidytuesdayR package 
## install.packages("tidytuesdayR")

tuesdata <- tidytuesdayR::tt_load('2023-08-22')
## OR
tuesdata <- tidytuesdayR::tt_load(2023, week = 34)

population <- tuesdata$population

# Option 2: Read directly from GitHub

population <- readr::read_csv('https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2023/2023-08-22/population.csv')
```
### Cleaning Script

``` r
### Data from the {refugees} R package

library(tidyverse)
library(refugees)

populations <- refugees::population

# Get just the years from 2010 to 2022

populations2010 <- filter(populations, year >= 2010)

write_csv(populations2010, "population.csv")
```

## Variable Names and Descriptions:

- **year:** The year
- **coo_name Country:** of origin name
- **coo:**	Country of origin UNHCR code
- **coo_iso:**	Country of origin ISO code
- **coa_name:**		Country of asylum name
- **coa:**		Country of asylum UNHCR code
- **coa_iso:**		Country of asylum ISO code
- **refugees:**		The number of refugees
- **asylum_seekers:**		The number of asylum-seekers
- **returned_refugees:**	The number of returned refugees
- **idps:**		The number of internally displaced persons
- **returned_idps:**		The number of returned internally displaced persons
- **stateless:**		The number of stateless persons
- **ooc:**		The number of others of concern to UNHCR
- **oip:**	The number of other people in need of international protection
- **hst:**		The number of host community members

## Data Types:

- **year:** double
- **coo_name Country:** character
- **coo:**	character
- **coo_iso:**	character
- **coa_name:**	character
- **coa:**	character
- **coa_iso:**	character
- **refugees:**	double
- **asylum_seekers:**		double
- **returned_refugees:**	double
- **idps:**		The number double
- **returned_idps:**		double
- **stateless:**		double
- **ooc:**		double
- **oip:**	double
- **hst:**		double

- ## Full Preview of Dataset
  
|variable          |class     |description       |
|:-----------------|:---------|:-----------------|
|year              |double    |The year.              |
|coo_name          |character |Country of origin name.        |
|coo               |character |Country of origin UNHCR code.   |
|coo_iso           |character |Country of origin ISO code.  |
|coa_name          |character |Country of asylum name.    |
|coa               |character |Country of asylum UNHCR code.  |
|coa_iso           |character |Country of asylum ISO code.    |
|refugees          |double    |The number of refugees.   |
|asylum_seekers    |double    |The number of asylum-seekers.  |
|returned_refugees |double    |The number of returned refugees. |
|idps              |double    |The number of internally displaced persons.     |
|returned_idps     |double    |The number of returned internally displaced persons.  |
|stateless         |double    |The number of stateless persons.  |
|ooc               |double    |The number of others of concern to UNHCR.   |
|oip               |double    |The number of other people in need of international protection.     |
|hst               |double    |The number of host community members.     |



