# Overview
The EU ETS keeps track of transaction, account, and compliance information on the EUTL website: https://ec.europa.eu/clima/ets/welcome.do. The site allows users to search for data and download it as XML files by clicking the “Export” button. However, there are limits on how much data can be downloaded at once, via a single XML file (<3000 entries). By searching for specific types of data entries (Transactions from Bulgaria from 2012-2013, for example), you can limit the number of results to less than 3000, enabling XML downloads. This process would be very tedious and time intensive to do manually, so automating these downloads is especially valuable. The following sections explain how this can be done.
Workflow scripts
The scripts below should be done in order to appropriately link the data files:
Download and parse the Transactions XML data:
T1_transaction-xmls-byregistry-bydate_DOWNLOAD.ipynb
T2_transaction-xmls-highvolume-days_DOWNLOAD.ipynb
T3_transaction-xmls-byregistry-bydate_PARSE.ipynb

Web-scrape the AccountIDs for the transferring and acquiring accounts involved in each transaction using the transactions XML data from step 1.
A0_AccountID-crawler_SCRAPE.ipynb

Download and parse the Accounts and Operators XML data using the unique AccountIDs you scraped in step 2.
A1_xml-accounts-byaccountID.ipynb
A2_xml-accounts-byaccountID_PARSE.ipynb
O1_xml-operators-byaccountID.ipynb
O2_xml-operators-byaccountID_PARSE.ipynb

Additionally, the Accounts and Operator Holding Account data can be separately downloaded (but not linked) with the following scripts:
xml-accounts-byregistry-bytype.ipynb
xml-operators-byregistry.ipynb


