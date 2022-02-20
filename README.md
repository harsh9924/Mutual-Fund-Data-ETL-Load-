# Mutual-Fund-Data-ETL-Load-
## Problem Statement  Design an ingestion pipeline to fetch Mutual Fund data from the [AMFI](https://www.amfiindia.com/nav-history-download) website, model, and store that data into a database for further processing.

My stepwise Approach

Gathering Knowledge(to find the best solution) and understanding the task=

-A data pipeline architecture is layered. Each subsystem feeds into the next until data reaches its destination.
-Data ingestion is the transportation of data from assorted sources to a storage medium where it can be accessed, used, and analyzed by an organization.
-Types of Data Ingestion: batch processing(most common), stream processing, micro batching (To be used because we need incremental data).
-The main task was to find the endpoints of the API (For tracking the back history of data) and create a pipeline that executes the flow properly.

Execution wise Explanation--

condition 1 (The pipeline should be able to do a full load, to begin with, and then fetch the incremental data every day.)
-Fetching data using URL
 URL example - https://portal.amfiindia.com/DownloadNAVHistoryReport_Po.aspx?frmdt=20-FEB-2022
 Coding in such a way that (frmdt) is incremented every day.
 
 Condition 2 (Modeling the data and choice of database is left to you.)
- Modeling the data(creating a visual representation for understanding the relationship between the data).
- Open Ended Schemes (Debt Scheme(Banking and PSU Fund, Corporate Bond Fund,...));
                     (Equity Scheme(Contra Fund,Dividend Yield Fund,..));
                     (Floating Rate);(Gilt);
                     (Growth);
                     (Hybrid Scheme(Aggressive Hybrid Fund,..));
                     (Income);
                     (Money Market);
                     (Other scheme(For Domestic,..));
                     (Solution Oriented Scheme(Childrenâ€™s Fund,..);
Interval Fund Schemes (Growth);
                      (Income);
Close Ended Schemes (ELSS);
                    (Growth);
                    (Income);
Database - Mysql

Condition 3 (The pipeline should be able to deal with failures and should be designed to fetch and store data in a performance-efficient manner.)
-The Failure we can expect is the server down, at that time the extracted data should remain safe and should give a message about the issue on the server.

Flow–
1-Extract data through URL.
2-Design for extracting data in an incremental manner.
3-Understand the data format and code for the segregation of data into tables and columns. (Number of spaces and a particular format)
4-Establishing Connection with Mysql Server and then storing data 
5-If an error occurs display a message.
