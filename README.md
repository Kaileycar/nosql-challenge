# NoSQL Challenge

The UK Food Standards Agency evaluates various establishments across the UK and gives them a  
food hygiene rating. You've been contracted by the editors of *Eat, Safe, Love* magazine to  
evaluate the ratings data to help food critics decide where to focus future food articles. You  
will be updating a database in Jupyter Notebook in parts 1 and 2. In part 3, you will preform  
an exploratory analysis to help answer 4 questions.

---

## About

The purpose of this assignment is to import MonogDB into Jupyter Notebook to evaluate and  
analyze establishment hygiene ratings. `Part 1` sets up the Database and imports the data into  
your Jupyter Notebook. `Part 2` is about updating the data in the Database. You first want to update  
the Database to add one more establishment to the *establishments* collection. Next, update the  
datatypes of the `longitutde`, `latitude`, and `RatingValue` to be decimal numbers or integers.  
`Part 3` is about creating an exploratory analysis to answer 4 questions...  

  1. Which establishments have a hygiene score equal to 20?
  2. Which establishments in London have a RatingValue greater than or equal to 4?
  3. What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest
     to the new restaurant added, "Penang Flavours"?
  4. How many establishments in each Local Authority area have a hygiene score of 0? Sort the results
     from highest to lowest, and print out the top ten local authority areas.

---

## Getting Started

1. Create a new repository for this project called `nosql-challenge`.
2. Clone the new repository to your computer.
3. Add your Jupyter notebook starter files and your `Resources` folder containing `establishments.json`
4.  to this folder.

5.  Download the [Starter_Code](https://github.com/Kaileycar/nosql-challenge/files/12164812/Starter_Code.zip) to get started.

---

## Usage

### Part 1: Database and Jupyter Notebook Set Up  
### Part 2: Update the Database  

* Use the `NoSQL_setup_starter.ipynb` for these sections.
* Make sure to set the database and collection to a variable.
* The `latitude` and `longitude` should be converted to decimals and the `RatingValue` should be converted
  to an integer.
* Use the following information to add and update one more establishment to the collection.
  
  `{  
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
}`   

### Part 3: Exploratory Analysis  

* Use the `NoSQL_analysis_starter.ipynb` for this section.
* The `RatingValue` refers to the overall rating of the establishment that ranges from 1-5.
  The higher the value, the better the rating.
  
    * **Note**: This field also includes non-numeric values such as 'Pass', where 'Pass' means
                that the establishment passed their inspection but isn't given a number rating.
                We will coerce non-numeric values to nulls during the database setup before
                converting ratings to integers.

* The scores for `Hygiene`, `Structural`, and `ConfidenceInManagement` work in reverse. This means,
  the higher the value, the worse the establishment is in these areas.
* The London Local Authority has a longer name than "London" so you will need to use `$regex` as part of your search.
* You will need to compare the geocode to find the nearest locations. Search within `0.01` degree on either side
  of the latitude and longitude.
* You will need to use the `aggregation` method to answer question 4.
    * When sorting the values, make sure to sort in `descending` order.  
    * The top 5 rows of your DataFrame for question 4 should look like this:
 
      |          | **_id**      |**count**      |
      |:--------:|:------------:|:-------------:|
      | 0        | Thanet       | 1130          |
      | 1        | Greenwich    | 882           |
      | 2        | Maidstone    | 713           |
      | 3        | Newham       | 711           |
      | 4        | Swale        | 686           |



