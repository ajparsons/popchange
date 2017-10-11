<!-- can be complied locally with pandoc process-for-running-code.md -s -o process-for-running-code.html -->

# Process for Generating Grids

These scripts allow you to take any Census attribute for any Census year (1971 - 2011) and convert it to a regular 1km grid across Great Britain. This document outlines the setup and the steps to create the grids. 
 
## Setup Program and Data

- Setup R & RStudio *(detailed instructions available [here](https://github.com/ClearMappingCo/installing-software/blob/master/installing-r-rstudio.Rmd))*  
- Install these libaries using `install.libaries("*library_name*")
- - `maptools`, `rgdal`, `rgeos` and `raster`.   
- Download (or clone) the repoisitory from GitHub.  
- Open `popchange.Rproj` file (RStudio project file).  
- Download the data for the input folder from [https://popchange-data.liverpool.ac.uk/script-data/input-data.zip](https://popchange-data.liverpool.ac.uk/script-data/input-data.zip) (109 MB)  
- In the `input` folder, unzip the `input-data.zip` file. This should add a number of folders to the input folder. *This includes the OA proportions and example attribute data files (mentioned below).*  

## Download and Prepare Census data

Prepare the Census data you wish to use. An example of this file is at `input\1991\attributes\1991-OA-attributes-sas01.csv`. This file is loaded the script [analysis-no-overlay.R](analysis-no-overlay.R) on line 41. This is a CSV file containing a list of all the OAs or EDs (depending on the census year) and the one or more attributes you wish to create a grid for. One grid will be created for each attribute you enter. For example:

|  GeographyCode | PresRes  |  TotalPop | EtWh  |  EtBlCab |
| --- | --- | --- | --- | --- |
| 01AAFA01 | 256 | 349 | 312 | 2   | 
| 01AAFA02 | 132 | 156 | 134 | 1   | 
| 01AAFA03 | 182 | 229 | 221 | 0   | 
| 01AAFA04 | 0 | 0 | 0 | 0   | 
| 01AAFA05 | 272 | 327 | 304 | 0   | 

Important things to note:  

- The first column *must* be called "GeographyCode".  
- You can have any number of columns (but for each column you have, the processing will take longer).  
- Attribute column names need to 10 characters or less to support the shapefile format.  

It is important that your input CSV file is within the `input` folder. How you organise it beneath that is up to you. You can see the structure I have used previously, imported from the `input-data.zip` file. The `xxxx-OA-grid-proportion.csv` and `xxxx-contiguous-regions.RData` files are within an appropriate folder for each year (where xxxx is the year). I would recommend you put your attribute file in the attributes folder within each year. 

If you wish to calculate grids for another variable, you can download Census data from a numner of different sites. Here are the sources used for this project, and some associated notes:  

- **1971 - 2001** Casweb [http://casweb.ukdataservice.ac.uk](http://casweb.ukdataservice.ac.uk)  
- - For 1971, need to prepare the data as below, and then run code to allocate 71 EDs to 81 EDs as per script [lookup71-81.R](lookup71-81.R).  
- - For 1991, some tables are structured differently and so you need to download separately and combine them combine them into one file (usually the variable structure matches for England and Wales, and is similar for Scotland).  
- - For 2001, you need to download England, Scotland and Wales separately and combine them into one file (usually the variable structure matches for England and Wales, and is similar for Scotland).  

- **2011**
- - Download England & Wales data from Nomis [https://www.nomisweb.co.uk/census/2011/bulk/r2_2](https://www.nomisweb.co.uk/census/2011/bulk/r2_2).  
- - Download Scotland data from Scotland Census [http://www.scotlandscensus.gov.uk/ods-web/data-warehouse.html#bulkdatatab](http://www.scotlandscensus.gov.uk/ods-web/data-warehouse.html#bulkdatatab).  
- - *Some Scotland variables are ordered very differently (e.g. Country of Birth & Ethnicity). Combine these carefully!*  
- - Also replace '-' in Scotland 11 with '0', using Find and Replace. This is easiest done in a text editor (e.g. TextWrangler ot Notepad) than LibreOffice Calc because of the size of the file.  

When working out the field names to go into the OA-attributes CSV file, remember to make sure they are 10 characters or less. See the example in `input\1991\attributes\1991-OA-attributes-sas01.csv`. 

*If you are creating a series of grids for additional Census variables, we are very happy to host them on the PopChange website (either in the tool itself, or on the Data download tab). Please contact us for more information on how to get the data to us.*  

## Update & Run code

Update lines 41-47 of `analysis-no-overlay.R` to update the variable name, year and grid input. I usually then run lines 41 and 43 to read in the data and check field names are all correct. 

Run all of the code in `analysis-no-overlay.R` *Select all the text (Ctrl-A) and then click run (or Ctrl-Enter)*.  

## Check Output

A series of files will be created in the output folder. Check the files to see if they are what you expect!

If it doesn't work, or you get an error message, check the [FAQs](faq.md). 