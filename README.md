This script queries a csv formatted export feed file and exports all records from it to another csv file based on the defined status to search for in a specific column. Approved is the default status to search for.

**How it works**
- On windows, go to the dir with the script and source file and run the cmd "python3.exe .\ParseExport.py SrcExportFile.csv"
- The source file will first be copied to a backup file called  "<src_filename>_<TIMESTAMP>.csv" e.g. SrcExportFile_2024-08-20-22-31-56.csv in case of problems
- Previously generated output files will be backed up as "<src_filename>-<Status>__<TIMESTAMP>.csv" e.g. SrcExportFile-Approved_2024-08-20-22-37-15.csv
- It will detect the column number where the first occurrence of the Search Status keyword e.g. Approved occurs and prompt the user to check this is the correct column before continuing
- Assuming the user continues, it will first count how many instances of transactions in the src file match the search status keyword
- It will parse these records with the required status to a new csv file called "<src_filename>-<Status>.csv" e.g. SrcExportFile-Approved.csv
- It will finally do a basic validation that the number of occurrences in the src file match those in the dest file.

**caveats..**
CSVs are a pain to parse. If there is a column before the status column which has a , as an entry in the cell vs. as a delimiter, the script will miss the cell with the status i.e. miss the record
I cannot guarantee it will fully work given the nature of csv files but hope it helps.
