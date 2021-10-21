# Attempt to import Agribalyse to a brightway2 database

## Data source
- CSV files from https://www.data.gouv.fr/fr/datasets/agribalyse
- alternatively from https://nexus.openlca.org/database/Agribalyse 

[the files from data.gouv.fr are the files from the Nexus OpenLCA converted to a more easily readable format, i.e. csv files]

## CSV file structure 

Tables are explained at https://www.data.gouv.fr/fr/datasets/agribalyse
More info from the methodology page https://doc.agribalyse.fr/documentation/?cacheBust=1634652873522 

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
