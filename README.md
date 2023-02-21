# YouTube Videos: Data Analysis With Python (pandas)
 Supplementary Material for my [YouTube Videos](https://youtube.com/playlist?list=PLCZPLPOZkkjaTIDFjWmMWZZrsazv15z_J)

## File Descriptions <a name="files"></a>

`data/AC2021_AnnualisedEntryExit.xlsx`   
Excel file taken straight from the [TfL website]( http://crowding.data.tfl.gov.uk/Annual%20Station%20Counts/2021/AC2021_AnnualisedEntryExit.xlsx).   
The first sheet in the file explains the contents: "The station entry / exit counts in this file represent the entry / exit or boarding / alighting count at each station on a typical weekday (Monday-Thursday), Friday, Saturday or Sunday, and annualised to an annual entry / exit total."

`1 Data-Cleaning.ipynb`     
This is the Jupyter notebook we use in the YouTube videos for data cleaning.

`Load_Excel_Data_In_Pandas.ipynb`  
In the YouTube videos, we (1) perform the initial cleaning in Excel (2) save the file as a CSV file, and (3) load the CSV file using pandas.
In this notebook, we avoid the use of MS Excel altogether and do all the initial steps in Python using the openpyxl library. 

Although I do a walkthrough of the code in the notebook, it turns out to just be 5 lines of code:
```
import pandas as pd
df = pd.read_excel('AC2021_AnnualisedEntryExit.xlsx', sheet_name="Annualised", skiprows = 5, header = [0,1])
df.columns = [' '.join(col).strip() for col in df.columns.values]
df.columns = df.columns.str.replace('Unnamed: \d+_level_0 ', '', regex=True)
df[df.columns[6:14]] = df[df.columns[6:14]].astype('int32') 
```

`Webscraping_Demonstration_pandas_read_html.ipynb`   
This notebook demonstrates the simplest method of getting data that is in the form of tables on web pages. 
