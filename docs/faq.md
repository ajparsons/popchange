# FAQs

Here are some answers to common error messages or frequently asked questions:

## Sample output data

If you are having trouble running the code, there is some sample output data at (https://popchange-data.liverpool.ac.uk/script-data/sample-output-data.zip) (34 MB). To run the sample data (1991 Total Population data) took 155.05 seconds (as reported in the script) on my machine (Windows 7, Intel Core i7-6700K 4GHz, 32GB RAM, saving to local storage) on 11/10/2017. 

## Error messages

If you get a whole bunch of error messages, scroll back up in the Console to see where the first error message was. Deal with this, and try to run the code again. It will probably solve all of the other errors. 

## Dropbox

If you store the data files in a Dropbox folder, then you can get file access problems (with R and Dropbox trying to access the file at the same time). Pause Dropbox before running the code. 

## Local storage

It is important to have the files stored on the local hard disk. Otherwise the file writing time may be (massively) extended if writing to a network drive. E.g. 10000 seconds compared to 155.05 seconds for the sample data.