# Crime Data API
Users of this API will be able to access  Uniform Crime Reporting data from 1979. The program’s goal is to generate reliable information for use in law enforcement administration, operations, and management.
The UCR Program consists of four data collections: The National Incident-Based Reporting System (NIBRS), the Summary Reporting System (SRS), the Law Enforcement Officers Killed and Assaulted (LEOKA) Program, and the Hate Crime Statistics Program. 
While it is powerful, the reporting participation is voluntary. Today,  UCR receives data from more than 18,000 city, university and college, county, state, tribal, and federal law enforcement agencies voluntarily participating in the program. 

Return data types:
	* 	JSON
	* CSV
There is no rate-limits or usage restrictions specified. However, the FBI strongly advises against using the data to do any comparison or ranking among cities or states.


## Get the API Key
You can get an API key at: https://api.data.gov/signup/

## Summary of Endpoints
	* summarized-data-controller : Endpoints pertaining to Agency SRS Level Crime Data
	* error-controller : Error Controller
	* supplemental-data-controller : Endpoints pertaining to Supplemental data
	* lookups-controller : Endpoints pertaining to CDE Related Lookup Value data
	* offense-tkm-controller : Endpoints pertaining to NIBRS Offense Demographic data
	* offender-tkm-controller : Endpoints pertaining to NIBRS Offender Demographic data
	* preliminary-tkm-controller : Endpoints pertaining to Preliminary Reportdata
	* police-employment-controller : Endpoints pertaining to UCR Police Employment data
	* victim-data-controller : Endpoints pertaining to NIBRS Victim Demographic data
	* foot-note-controller : Endpoints pertaining to Footnotes for UCR data sets
	* summarized-tkm-controller : Endpoints pertaining to UCR Agency SRS Level Crime Data
	* offender-data-controller : Endpoints pertaining to NIBRS Offender Demographic data
	* participation-controller : Endpoints pertaining to UCR Participation data
	* arrest-data-controller : Endpoints pertaining to Arrest Demographic data
	* offense-data-controller : Endpoints pertaining to NIBRS Offense Demographic data
	* preliminary-data-controller : Endpoints pertaining to Preliminary Reportdata
	* summary-controller : Endpoints pertaining to UCR Estimated Crime Data
	* arrest-tkm-controller : Endpoints pertaining to Arrest Demographic data
	* victim-tkm-controller : Endpoints pertaining to NIBRS Victim Demographic data

For example, **summerized-data-controller** has three endpoints:
		* 	Agency level SRS Crime Data Endpoint:  `/api/summarized/agencies/{ori}/offenses/{since}/{until} `
		* Agency level SRS Crime Data Endpoint by Offense: `/api/summarized/agencies/{ori}/{offense}/{since}/{until} `
		* Agency level SRS Crime Data Endpoint by Offense: `/api/summarized/state/{stateAbbr}/{offense}/{since}/{until}`

Append the endpoint you want to use to the base API url: ‘https://api.usa.gov/crime/fbi/sapi’


## Sample Queries
A sample query in Python is as follows:

```
import json, requests

# you should replace the “SUBSTITUTE_YOUR_KEY” string with the # key obtained at: https://api.data.gov/signup/
url = 'https://api.usa.gov/crime/fbi/sapi/api/data/arrest/states/offense/NY/all/2015/2018?API_KEY=SUBSTITUTE_YOUR_KEY’

#get response from the endpoint
res= requests.get(url)

# read response data into json
data = json.loads(res.text)

# write data to the disk
with open(‘file_name_of_your_choice.json', 'w') as output:
    json.dump(data, output, indent=2)

```

Change url accordingly.

### Query 1: Get Agency List
You might want to get a full list of agencies first.
`https://api.usa.gov/crime/fbi/sapi/api/agencies/lis`
This endpoint does not take any parameter.

Truncated response:
```
[
  {
    "ori": "AK0010100",
    "agency_name": "Anchorage Police Department",
    "agency_type_name": "Municipality",
    "state_name": "Alaska",
    "state_abbr": "AK",
    "division_name": "Pacific",
    "region_name": "West",
    "region_desc": "Region IV",
    "county_name": "ANCHORAGE",
    "nibrs": false,
    "latitude": 61.17425,
    "longitude": -149.284329,
    "nibrs_start_date": null
  },
  {
    "ori": "AK0010200",
    "agency_name": "Fairbanks Police Department",
    "agency_type_name": "Borough",
    "state_name": "Alaska",
    "state_abbr": "AK",
    "division_name": "Pacific",
    "region_name": "West",
    "region_desc": "Region IV",
    "county_name": "FAIRBANKS NORTH STAR",
    "nibrs": false,
    "latitude": 64.83945,
    "longitude": -147.71942,
    "nibrs_start_date": null
  },
  {
    "ori": "AK0010300",
    "agency_name": "Juneau Police Department",
    "agency_type_name": "City and Borough",
    "state_name": "Alaska",
    "state_abbr": "AK",
    "division_name": "Pacific",
    "region_name": "West",
    "region_desc": "Region IV",
    "county_name": "JUNEAU",
    "nibrs": false,
    "latitude": 58.356556,
    "longitude": -134.50731,
    "nibrs_start_date": null
  },
  {
    "ori": "AK0010400",
    "agency_name": "Ketchikan Police Department",
    "agency_type_name": "Borough",
    "state_name": "Alaska",
    "state_abbr": "AK",
    "division_name": "Pacific",
    "region_name": "West",
    "region_desc": "Region IV",
    "county_name": "KETCHIKAN GATEWAY",
    "nibrs": false,
    "latitude": 55.449938,
    "longitude": -131.106685,
    "nibrs_start_date": null
  },
  {
    "ori": "AK0010500",
    "agency_name": "Kodiak Police Department",
    "agency_type_name": "Borough",
    "state_name": "Alaska",
    "state_abbr": "AK",
    "division_name": "Pacific",
    "region_name": "West",
    "region_desc": "Region IV",
    "county_name": "KODIAK ISLAND",
    "nibrs": false,
    "latitude": 57.8049,
    "longitude": -152.37332,
    "nibrs_start_date": null
  },
  {
    "ori": "AK0010600",
    "agency_name": "Nome Police Department",
    "agency_type_name": "Census Area",
    "state_name": "Alaska",
    "state_abbr": "AK",
    "division_name": "Pacific",
    "region_name": "West",
    "region_desc": "Region IV",
    "county_name": "NOME",
    "nibrs": false,
    "latitude": 64.783686,
    "longitude": -164.188912,
    "nibrs_start_date": null
  },
  {
    "ori": "AK0010700",
    "agency_name": "Petersburg Police Department",
    "agency_type_name": "Borough",
    "state_name": "Alaska",
    "state_abbr": "AK",
    "division_name": "Pacific",
    "region_name": "West",
    "region_desc": "Region IV",
    "county_name": "PETERSBURG",
    "nibrs": false,
    "latitude": 55.415683,
    "longitude": -132.875734,
    "nibrs_start_date": null
  },
  {
    "ori": "AK0010800",
    "agency_name": "Seward Police Department",
    "agency_type_name": "Borough",
    "state_name": "Alaska",
    "state_abbr": "AK",
    "division_name": "Pacific",
    "region_name": "West",
    "region_desc": "Region IV",
    "county_name": "KENAI PENINSULA",
    "nibrs": false,
    "latitude": 60.366668,
    "longitude": -152.322283,
    "nibrs_start_date": null
  },
  {
    "ori": "AK0010900",
    "agency_name": "Sitka Police Department",
    "agency_type_name": "City and Borough",
    "state_name": "Alaska",
    "state_abbr": "AK",
    "division_name": "Pacific",
    "region_name": "West",
    "region_desc": "Region IV",
    "county_name": "SITKA",
    "nibrs": false,
    "latitude": 57.052124,
    "longitude": -135.33418,
    "nibrs_start_date": null
  }
#truncated
]
```

### Query 2: State Level Arrest Data
`https://api.usa.gov/crime/fbi/sapi/api/data/arrest/states/offense/{stateAbbr}/{variable}/{since}/{until}?API_KEY=YOUR_KEY``

	* stateAbbr: NY, CA, etc
	* variable: all, monthly
	* since: year, eg 2015 (included)
	* until: year, eg 2018 (included)

Example: If you want to compare the arrest count year by year in New York State from 2015 to 2018:
`https://api.usa.gov/crime/fbi/sapi/api/data/arrest/states/offense/NY/all/2015/2018?API_KEY=SUBSTITUTE_YOUR_KEY`
Response:
```
{
  "results": [
    {
      "aggravated_assault": 8659,
      "all_other_offenses": 46879,
      "arson": 280,
      "burglary": 6387,
      "curfew": 0,
      "disorderly": 7254,
      "driving": 30102,
      "drug_abuse_gt": 60534,
      "drug_poss_m": 17038,
      "drug_poss_opium": 935,
      "drug_poss_other": 4958,
      "drug_poss_subtotal": 43260,
      "drug_poss_synthetic": 180,
      "drug_sales_m": 204,
      "drug_sales_opium": 1038,
      "drug_sales_other": 516,
      "drug_sales_subtotal": 2396,
      "drug_sales_synthetic": 24,
      "drunkness": 0,
      "embezzlement": 74,
      "forgery": 2780,
      "fraud": 5035,
      "g_all": 70,
      "g_b": 4,
      "g_n": 4,
      "g_t": 78,
      "ht_c_s_a": 0,
      "ht_i_s": 0,
      "larceny": 44925,
      "liquor": 1871,
      "manslaughter": 11,
      "mvt": 1804,
      "murder": 268,
      "offense_family": 598,
      "prostitution": 867,
      "prostitution_a_p_p": 0,
      "prostitution_p": 0,
      "prostitution_p_p": 0,
      "rape": 1162,
      "robbery": 3628,
      "sex_offense": 2000,
      "simple_assault": 31315,
      "stolen_property": 3733,
      "suspicion": 0,
      "vagrancy": 731,
      "vandalism": 14871,
      "weapons": 3529,
      "csv_header": null,
      "data_year": 2015
    },
    {
      "aggravated_assault": 8757,
      "all_other_offenses": 44869,
      "arson": 242,
      "burglary": 5942,
      "curfew": 0,
      "disorderly": 6489,
      "driving": 29931,
      "drug_abuse_gt": 65878,
      "drug_poss_m": 18109,
      "drug_poss_opium": 1319,
      "drug_poss_other": 4632,
      "drug_poss_subtotal": 48909,
      "drug_poss_synthetic": 149,
      "drug_sales_m": 125,
      "drug_sales_opium": 1069,
      "drug_sales_other": 326,
      "drug_sales_subtotal": 2313,
      "drug_sales_synthetic": 15,
      "drunkness": 0,
      "embezzlement": 64,
      "forgery": 2850,
      "fraud": 4476,
      "g_all": 59,
      "g_b": 13,
      "g_n": 2,
      "g_t": 74,
      "ht_c_s_a": 0,
      "ht_i_s": 0,
      "larceny": 42499,
      "liquor": 1608,
      "manslaughter": 18,
      "mvt": 1856,
      "murder": 263,
      "offense_family": 606,
      "prostitution": 632,
      "prostitution_a_p_p": 0,
      "prostitution_p": 0,
      "prostitution_p_p": 0,
      "rape": 1122,
      "robbery": 3333,
      "sex_offense": 2008,
      "simple_assault": 30086,
      "stolen_property": 3524,
      "suspicion": 0,
      "vagrancy": 566,
      "vandalism": 15019,
      "weapons": 3670,
      "csv_header": null,
      "data_year": 2016
    },
    {
      "aggravated_assault": 8480,
      "all_other_offenses": 43464,
      "arson": 297,
      "burglary": 5414,
      "curfew": 0,
      "disorderly": 5499,
      "driving": 27940,
      "drug_abuse_gt": 71263,
      "drug_poss_m": 48396,
      "drug_poss_opium": 6684,
      "drug_poss_other": 15282,
      "drug_poss_subtotal": 68251,
      "drug_poss_synthetic": 831,
      "drug_sales_m": 521,
      "drug_sales_opium": 1908,
      "drug_sales_other": 1895,
      "drug_sales_subtotal": 4233,
      "drug_sales_synthetic": 83,
      "drunkness": 0,
      "embezzlement": 48,
      "forgery": 2676,
      "fraud": 4335,
      "g_all": 91,
      "g_b": 11,
      "g_n": 0,
      "g_t": 102,
      "ht_c_s_a": 0,
      "ht_i_s": 0,
      "larceny": 38337,
      "liquor": 1476,
      "manslaughter": 13,
      "mvt": 1793,
      "murder": 269,
      "offense_family": 552,
      "prostitution": 685,
      "prostitution_a_p_p": 0,
      "prostitution_p": 0,
      "prostitution_p_p": 0,
      "rape": 999,
      "robbery": 3199,
      "sex_offense": 1752,
      "simple_assault": 28451,
      "stolen_property": 3319,
      "suspicion": 0,
      "vagrancy": 626,
      "vandalism": 14111,
      "weapons": 3546,
      "csv_header": null,
      "data_year": 2017
    },
    {
      "aggravated_assault": 7791,
      "all_other_offenses": 39810,
      "arson": 272,
      "burglary": 4446,
      "curfew": 0,
      "disorderly": 4932,
      "driving": 25684,
      "drug_abuse_gt": 70575,
      "drug_poss_m": 46726,
      "drug_poss_opium": 6645,
      "drug_poss_other": 15067,
      "drug_poss_subtotal": 67643,
      "drug_poss_synthetic": 654,
      "drug_sales_m": 446,
      "drug_sales_opium": 1522,
      "drug_sales_other": 1623,
      "drug_sales_subtotal": 3530,
      "drug_sales_synthetic": 59,
      "drunkness": 0,
      "embezzlement": 28,
      "forgery": 2118,
      "fraud": 4015,
      "g_all": 40,
      "g_b": 4,
      "g_n": 1,
      "g_t": 45,
      "ht_c_s_a": 0,
      "ht_i_s": 0,
      "larceny": 35341,
      "liquor": 983,
      "manslaughter": 11,
      "mvt": 1820,
      "murder": 250,
      "offense_family": 478,
      "prostitution": 583,
      "prostitution_a_p_p": 0,
      "prostitution_p": 0,
      "prostitution_p_p": 0,
      "rape": 955,
      "robbery": 2669,
      "sex_offense": 1779,
      "simple_assault": 27217,
      "stolen_property": 2861,
      "suspicion": 0,
      "vagrancy": 580,
      "vandalism": 12806,
      "weapons": 3210,
      "csv_header": null,
      "data_year": 2018
    }
  ],
  "pagination": {
    "count": 4,
    "page": 0,
    "pages": 1,
    "per_page": 0
  }
}
```

The result is self-explanatory.

### Query 3: Agency Level Crime Data by Offense
`https://api.usa.gov/crime/fbi/sapi/api/summarized/agencies/{ori}/{offense}/{since}/{until}?API_KEY=YOUR_KEY`

	* ori (Originating Agency Identifier) of New York City Police Department;
	* offense: choose among: aggravated-assault, burglary, larceny, motor-vehicle-theft, homicide, rape, robbery, arson, violent crime, property crime;
	* since: year, eg 2015 (included)
	* until: year, eg 2018 (included)

Example: if you want to find New York City Police department’s burglary data from 2015 to 2019:
`https://api.usa.gov/crime/fbi/sapi/api/summarized/agencies/NY0303000/burglary/2015/2018?API_KEY=SUBSTITUTE_YOUR_KEY`
The ori of NYC Police Department is NY0303000
The offense is burglary

Response:
```
{
  “results”: [
    {
      “ori”: “NY0303000”,
      “data_year”: 2015,
      “offense”: “burglary”,
      “state_abbr”: “NY”,
      “cleared”: 3765,
      “actual”: 14098
    },
    {
      “ori”: “NY0303000”,
      “data_year”: 2016,
      “offense”: “burglary”,
      “state_abbr”: “NY”,
      “cleared”: 3501,
      “actual”: 12041
    },
    {
      “ori”: “NY0303000”,
      “data_year”: 2017,
      “offense": "burglary",
      "state_abbr": "NY",
      "cleared": 3256,
      "actual": 11104
    },
    {
      "ori": "NY0303000”,
      “data_year”: 2018,
      “offense”: “burglary”,
      “state_abbr”: “NY”,
      “cleared": 3646,
      "actual": 10837
    }
  ],
  "pagination": {
    "count": 4,
    "page": 0,
    "pages": 1,
    “per_page”: 0
  }
}
```


