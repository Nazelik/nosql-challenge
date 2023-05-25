# nosql-challenge


The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. The editors of a food magazine, Eat Safe, Love, ask to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.
This assignment consists of three parts:
Part 1: Database and Jupyter Notebook Set Up
Part 2: Update the Database
Part 3: Exploratory Analysis

<br/><br/>

##  Part 1: Database and Jupyter Notebook Set Up
<br/>


'NoSQL_setup_starter.ipynb' is used for this section of the challenge.


* The data provided in the establishments.json file is imported. The database is named 'uk_food' and the collection is named 'establishments'. 
* All the necessary libraries are imported.
* An instance of the Mongo Client is created.
* Confirmed that the database is created and the data is loaded properly by listing the new created database and collections, and displaying one document from 'establishments' collection.
<br/><br/>


##  Part 2: Part 2: Update the Database
<br/>


'NoSQL_setup_starter.ipynb' is used for this section of the challenge.

The magazine editors had some requested modifications for the database before performing any queries or analysis for them. The following changes are performed to the establishments collection:

* An exciting new halal restaurant just opened in Greenwich, but hasn't been rated yet. The magazine had asked to include it in the analysis. The following information is added to the database:
   
   {
    "BusinessName":"Penang Flavours",
    "BusinessType":"Restaurant/Cafe/Canteen",
    "BusinessTypeID":"",
    "AddressLine1":"Penang Flavours",
    "AddressLine2":"146A Plumstead Rd",
    "AddressLine3":"London",
    "AddressLine4":"",
    "PostCode":"SE18 7DY",
    "Phone":"",
    "LocalAuthorityCode":"511",
    "LocalAuthorityName":"Greenwich",
    "LocalAuthorityWebSite":"http://www.royalgreenwich.gov.uk",
    "LocalAuthorityEmailAddress":"health@royalgreenwich.gov.uk",
    "scores":{
        "Hygiene":"",
        "Structural":"",
        "ConfidenceInManagement":""
    },
    "SchemeType":"FHRS",
    "geocode":{
        "longitude":"0.08384000",
        "latitude":"51.49014200"
    },
    "RightToReply":"",
    "Distance":4623.9723280747176,
    "NewRatingPending":True
}
<br/>


* The BusinessTypeID is found for "Restaurant/Cafe/Canteen" and returned only the BusinessTypeID and BusinessType fields.

* Updated the new restaurant with the BusinessTypeID.

* The magazine was not interested in any establishments in Dover, so  'how many documents contain the Dover Local Authority' was checked. Then, any establishments within the Dover Local Authority got removed from the database, and the number of documents ischecked to ensure they were deleted.

* Some string values are converted to numeric values.

<br/>


##  Part 3: Exploratory Analysis
<br/>


Eat Safe, Love had specific questions they wanted to get the answers, which are helpfull to find the locations to visit and avoid.

'NoSQL_analysis_starter.ipynb' is used for this section of the challenge.

Some notes:

RatingValue refers to the overall rating decided by the Food Authority and ranges from 1-5. The higher the value, the better the rating.
Note: This field also includes non-numeric values such as 'Pass', where 'Pass' means that the establishment passed their inspection but isn't given a number rating. We will coerce non-numeric values to nulls during the database setup before converting ratings to integers.
The scores for Hygiene, Structural, and ConfidenceInManagement work in reverse. This means, the higher the value, the worse the establishment is in these areas.

The following questions are used to explore the database, and find the answers:

* Which establishments have a hygiene score equal to 20?

* Which establishments in London have a RatingValue greater than or equal to 4?

* What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?

* How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas.


<br/><br/>

## Setup   
 'establishments_analysis' folder is consists of 'NoSQL_setup_starter.ipynb' and   'NoSQL_analysis_starter.ipynb' Jupiter notebooks which are the executables of this assignment and 'Resources' folder which contains 'establishments.json' resource file. 

 In order to run this code the following steps are needed:

 1.  Create a database and name it `uk_food` and the collection `establishments`.
 2. From your Terminal cd the directory/folder where Resources folder is located.
 3. Import the data provided in the `establishments.json` file from your Terminal using this command:

 ! mongoimport --type json -d uk_food -c establishments --drop --jsonArray Resources/establishments.json


<br/><br/>


## References
This project is a part of UC Berkeley "Data Analysis and Visualisation" Boot Camp education services.

In projects' descriptions, some paragraphs are copy/pasted from 'Module 11 Challenge' of UC Berkeley Data Analytics and Visualisation Bootcamp course.
 
May-24-2023
# nosql-challenge