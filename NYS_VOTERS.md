
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
|Region|Dem|Green|Work|Rep|Con|Libert|Blank|Indep|Other|Total|
|Capital|273,104|1,558|5,195|206,949|18,005|1,711|208,181|29,185|3,609|747,497|
|Central|166,630|1,124|2,389|161,362|9,755|1,345138,200 	 18,963 	 1,237 	 501,005 
Finger Lakes 	 274,870 	 1,595 	 3,288 	 250,045 	 15,387 	 2,349 	 210,150 	 26,203 	 684 	 784,571 
Hudson Valley 	 661,495 	 2,377 	 6,234 	 363,505 	 25,295 	 1,873 	 401,948 	 48,231 	 3,527 	 1,514,485 
Long Island 	 735,933 	 2,535 	 6,196 	 625,769 	 29,757 	 2,507 	 575,927 	 57,527 	 4,767 	 2,040,918 
Mohawk Valley 	 81,627 	 602 	 1,217 	 118,902 	 5,572 	 792 	 70,013 	 13,228 	 490 	 292,443 
New York City	 3,031,007 	 4,817 	 18,263 	 479,628 	 18,430 	 2,695 	 939,270 	 69,523 	 16,361 	 4,579,994 
North Country 	 71,988 	 440 	 995 	 94,400 	 3,759 	 471 	 59,333 	 10,436 	 493 	 242,315 
Southern Tier 	 128,093 	 993 	 2,014 	 148,080 	 5,970 	 1,197 	 92,348 	 15,006 	 1,882 	 395,583 
Western  	 372,023 	 1,877 	 5,963 	 267,173 	 22,737 	 2,153 	 215,045 	 29,010 	 1,875 	 917,856 
	 5,796,770 	 17,918 	 51,754 	 2,715,813 	 154,667 	 17,093 	 2,910,415 	 317,312 	 34,925 	 12,016,667

 ![image](https://github.com/user-attachments/assets/cfd9f410-e2f5-425d-a0b5-32b51a8a5a2b)

|----|----:|----:|----:|----:|----:|----:|----:|----:|----:|---:|
|Capital|292,504|1,798|5,464|220,234|18,907|1,930|222,140|32,416|3,659|**799,052**|
|Central|179,451|1,272|2,480|171,700|10,404|1,486|149,356|20,803|1,037|**537,989**|
|Finger Lakes|300,168|1,839|3,481|265,706|16,473|2,669|227,501|29,194|786|**847,817**|
|Hudson Valley|718,432|2,744|6,429|394,910|27,325|2,172|439,175|55,153|3,699|**1,650,039**|
|Long Island|794,821|2,927|6,579|669,728|31,958|2,940|613,407|64,854|3,416|**2,190,630**|
|Mohawk Valley|88,768|693|1,305|125,935|5,985|900|75,475|14,835|540|**314,436**|
|New York City|3,424,057|6,200|19,409|528,001|20,459|3,626|1,051,028|84,968|18,005|**5,155,753**|
|North Country|78,744|502|1,072|100,594|4,026|571|66,417|11,723|576|**264,225**|
|Soutehrn Tier|145,126|1,158|2,248|160,342|6,450|1,376|103,401|17,252|2,206|**439,559**|
|Western|399,871|2,093|6,249|282,282|23,964|2,418|228,591|31,862|2,080|**979,410**|
|**TOTAL**|**6,421,942**|**21,226**|**54,716**|**2,919,432**|**165,951**|**20,088**|**3,176,491**|**363,060**|**36,004**|**13,178,910**|

##### Distribution of Voters by County
|County|Number|
|:----|----:|
|**_Capital_**|**_799,052_**|
|Albany|212,693|
|Columbia|50,951|
|Greene|35,586|
|Rensselaer|111,702|
|Saratoga|190,703|
|Schenectady|106,922|
|Warren|50,279|
|Washington|40,216|
|**_Central_**|**_537,989_**|
|Cayuga|51,462|
|Cortland|32,070|
|Madison|47,330|
|Onondaga|327,781|
|Oswego|79,346|
|**_Finger Lakes_**|**_847,817_**|
|Genesee|39,771|
|Livingston|42,803|
|Monroe|531,701|
|Ontario|83,458|
|Orleans|25,872|
|Seneca|21,706|
|Wayne|61,846|
|Wyoming|25,921|
|Yates|14,739|
|**_Hudson Valley_**|**_1,650,039_**|
|Dutchess|224,340|
|Orange|265,467|
|Putnam|76,976|
|Rockland|221,299|
|Sullivan|54,393|
|Ulster|136,558|
|Westchester|671,006|
|**_Long Island_**|**_2,190,630_**|
|Nassau|1,068,950|
|Suffolk|1,121,680|
|**_Mohawk Valley_**|**_314,436_**|
|Fulton|35,855|
|Herkimer|44,506|
|Montgomery|31,124|
|Oneida|142,554|
|Otsego|38,796|
|Schoharie|21,601|
|**_New York City_**|**_5,155,753_**|
|Bronx|786,456|
|Kings|1,617,274|
|New York|1,112,476|
|Queens|1,304,648|
|Richmond|334,899|
|**_North Country_**|**_264,225_**|
|Clinton|53,351|
|Essex|27,256|
|Franklin|28,933|
|Hamilton|4,388|
|Jefferson|65,656|
|Lewis|19,625|
|St.Lawrence|65,016|
|**_Southern Tier_**|**_439,559_**|
|Broome|142,206|
|Chemung|55,956|
|Chenango|31,670|
|Delaware|31,710|
|Schuyler|13,404|
|Steuben|64,633|
|Tioga|34,732|
|Tompkins|65,248|
|**_Western_**|**_979,410_**|
|Allegany|27,584|
|Cattaraugus|51,669|
|Chautauqua|85,021|
|Erie|663,241|
|Niagara|151,895|
|**GRAND TOTAL**|**13,178,910**|
