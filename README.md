## Market data

This repository contains all data used to produce the results in the following paper:

**Pre-selection of assets for cardinality constrained index tracking portfolios**

The market data used in the paper consists of S&P500 assets, with prices ranging from 03 January 2005 up to 29 December 2023. The data accounts for survivalship buas and is organised in three files:

 - `SP500_assets.csv`: A csv file containing the list of assets that were part of the S&P500 index during (at least part of) this period. The file contains the following columns:
   - **TICKER**: Asset unique ticker
   - **NAME**: Asset name
   - **DATES_IN**: All the dates when the asset was added from the index. Dates are written in the format YYYYMMDD and if the company was added more than once, the field is separated by "-" (hyphen), such as YYYYMMDD-YYYYMMDD-... The dates are given in chronological order. Only dates from 01/01/2005 are included.
   - **DATES_OUT**: All the dates when the asset was removed from the index. Dates are written in the format YYYYMMDD and if the company was removed more than once, the field is separated by "-" (hyphen), such as YYYYMMDD-YYYYMMDD-... The dates are given in chronological order. Only dates from 01/01/2005 are included.
   - **SECTOR**: Sector to which each asset belongs.

 ```
   Example of how DATES_IN and DATES_OUT work:

     TICKER,...,DATES1,DATES2,...
     A1,...,,,...
     A2,...,20100101,20200101,...
     A3,...,20170202,20120403,...
     A4,...,20170202-20230801,20210101,...

   Asset A1 was already part of the index from 01/01/2005, and it is still in the index.
   Asset A2 was added to the index in 01/01/2010 and removed in 01/01/2020.
   Asset A3 was already part of the index in 01/01/2005, it was then removed in 03/04/2012 and added again in 02/02/2017.
   Finally, asset A4 was added to the index in 02/02/2017, removed in 01/01/2021 and added again on 01/08/2023.
 ```
 -  `SP500_daily.csv`: A csv file containing daily prices for the S&P500 and every asset in `assets.csv`. We use the **TICKER** as asset identifier (column names in the csv). A missing price means that the price did not exist at the time. A negative price means that the asset was not part of the S&P500 at the time.

 -  `SP500_weekly.csv`: A csv file containing weekly prices for the S&P500 and every asset in `assets.csv`. The format is the same as the file with the daily prices.
