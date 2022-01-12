# Attempt to import Agribalyse to a brightway2 database

## Data source for Agribalyse
- CSV files from https://www.data.gouv.fr/fr/datasets/agribalyse
- alternatively from https://nexus.openlca.org/database/Agribalyse 

Note: the files from data.gouv.fr are the files from the Nexus OpenLCA converted to a more easily readable format, i.e. csv files, according to data.gouv.fr

## CSV file structure 

Tables are explained at https://www.data.gouv.fr/fr/datasets/agribalyse
More info from the methodology page https://doc.agribalyse.fr/documentation/?cacheBust=1634652873522 

Note: according to [this person](https://github.com/lou-dupont/Agribalyse/commit/eea57713550a883662daaa03a531565223c43306), the table ```TBL_EXCHANGES.csv``` contains 3.5 million lines (one line, for one technosphere or environmental exchange). However, 75% of these are equal to 0 and useless to parse. Saves a lot of time to just filter them out before writing the database to brighway! (discovered at own expenses)


## Procedure

Inspired by Massimo's import for Exiobase.


1. Load all the CSV files as Pandas [done]
2. Identify all activities & products and create a dictionnary [done]
>> Issue here: the matrix is not square, there are more products than activities (missing activities can be replaced by dummy activities, hopefully)
3. Write the dictionnary as bw2 database [done]
4. Create a correspondance table between bw2's biosphere3 & the biosphere from Agribalyse [partly done, requires help/improvement]
>> Issue here: not so easy to get a 1-to-1 correspondance between the two, neither automatically, nor manually
5. Loop on all biosphere & technosphere exchanges, and save exchanges to the database [done]
>> Issue here: need speed improvement, need handling of issues (missing activities/products)
6. Do LCA calculations for all products/processes & validate them against implementation in SimaPro or openLCA [not done]
>> Validation is THE important step!