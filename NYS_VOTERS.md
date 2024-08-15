
#### NYS VOTERS
**_Overview_**  
In response to a Freedom of Information Law (FOIL) request, the New York State Board of Elections (BOE) provided in July 2024 a database containing information that BOE had on file for registered New York State voters (name = AllNYSVoters_20240722.txt). BOE has also provided a document mapping the layout of data files BoE provides in response to FOIL requests (name=FOIL_VOTER_LIST_LAYOUT.pdf).

**_Structure_**  
The database contains 47 fields of information:
* **4 fields** = segments of voter's full name
* **11 fields** = segments of voter's NYS address
* **4 fields** = segments of voter's alternative mailing address (if provided)
* **2 fields** = demographic information (_Date of Birth_ and _Gender_) about voter
* **2 fields** = party registration
* **8 fields** = voting districts
  * _County_
  * _Election district/Precinct code_
  * _Legislative district_
  * _Town_
  * _Ward_
  * _Congressional district_
  * _Senate district_
  * _Assembly district_
* **1 field** = last date voted (from BOE records)
* **4 fields** = self-provided infomration about previous registration (if provided)
* **5 fields** = information regarding registration application (ex. registration number)
* **4 fields** = voters' status (ex. active, purged, etc.)
* **1 field** = unique NYS Voter ID
* **1 field** = voter history

**_Modifications_**  
1. Each of the 47 fields was assigned the "Field Name" listed in the LAYOUT file BOE provided.
2. Each of New York's 62 counties is associated with an integer from 1 to 62; the "COUNTYCODE" field in the dataset contains the integer to identify the home county of the registered voter.  A separate csv file (NYS_CountyName_Region.csv) lists (a) the county name associated each code, and (b) the [region](https://en.wikipedia.org/wiki/Category:Regions_of_New_York_(state)) in which each county is located.  The AllNYSVoters_20240722.txt and NYS_CountyName_Regions.csv files were combined, adding two additional variables (one for COUNTYNAME, the other for REGION), bringing the number of fields to 49.
3. A new field (PARTY) created a single variable that combined the party affiliation information originally spread over two variables (ENROLLMENT and OTHER PARTY), bringing the total number of fields to 50.
4. The data file contains records not only for "Active" voters but also for "Inactive," "Purged," and "Pre-registered" voters.  Only "Active" voters were retained for use in subsequent analyses.  

**_Size_**  
The source data file provided by BOE contained a total of 13,316,724 records; 12,016,670 "Active" voters were extracted to create an analytic dataset for future use.

**_Summary of Dataset_**  
 
##### Distribution of Voters by Region and Party
![image](https://github.com/user-attachments/assets/a5af30b6-56e0-4a09-9359-62a4b8902491)

##### Distribution of Voters by County
![image](https://github.com/user-attachments/assets/e758b70f-4d6b-4e3b-8198-ff0d2663e299)

##### Distribution of Voters by Congressional District (CD) and Party
![image](https://github.com/user-attachments/assets/ca982dbf-6d5c-4676-866c-e2ff95aca744)

**_Output_**  
Revised source data files...in csv format (name=NYS_Voters_Jul24.csv) and Rdata format (name=NYS_Voters_Jul24.RData)...capturing the modifications above were created.  

**_Code_**  
R commands used to prepare the source data file and produce the summary of observations described above have been saved as Prep_NYSVoters_Jul24.R
