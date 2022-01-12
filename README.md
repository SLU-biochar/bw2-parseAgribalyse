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


1. Load all the CSV files as Pandas
2. Identify all activities and exchanges, and create a dictionnary
3. Write the dictionnary as bw2 database
4. Identify products of activities
5. Add the final prod to existing bw database
6. Import emissions from another xlsb file
7. Match emissions with biosphere3 codes (not all of them)
8. Add the emissions to the existing bw database
   
9. Do calculations.
