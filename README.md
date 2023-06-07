# UK Food Standards Agency Data Analysis
## Introduction
In this project, I have completed an analysis of the food hygiene ratings data provided by the UK Food Standards Agency. The objective of this analysis is to assist the editors of the food magazine, Eat Safe, Love, in identifying establishments for future articles. By evaluating the ratings data, I can provide insights to help the magazine's journalists and food critics decide where to focus their attention.

## Part 1: Database and Jupyter Notebook Set Up
To set up the database and Jupyter Notebook, I followed the instructions provided in the "NoSQL_setup_starter.ipynb" file. Here's what I accomplished:

1. Imported the data from the "establishments.json" file into a database named "uk_food" and a collection named "establishments" using the Terminal. Below is the command I used:
mongoimport --db uk_food --collection establishments --file establishments.json --jsonArray
2. Within the Jupyter Notebook, I imported the necessary libraries, including PyMongo and Pretty Print (pprint).
3. Created an instance of the Mongo Client to connect to the database.
4. Confirmed the successful creation of the database and data loading by performing the following steps:
* Listed the databases in MongoDB and verified that "uk_food" is listed.
* Listed the collections in the database to ensure that "establishments" is present.
* Retrieved and displayed one document from the "establishments" collection using the find_one method and pprint to ensure proper data retrieval.
5. Assigned the "establishments" collection to a variable to prepare it for further analysis.

## Part 2: Update the Database
In this section, I made the requested modifications to the "establishments" collection. These changes were necessary before proceeding with queries and analysis for the magazine editors. Here's what I did:

1. Added information about an exciting new halal restaurant, "Penang Flavours," to the database. The details of the restaurant, including its address and other attributes, were added as a new document with the "NewRatingPending" field set to True.
2. Found the BusinessTypeID for "Restaurant/Cafe/Canteen" and returned only the "BusinessTypeID" and "BusinessType" fields.
3. Updated the new restaurant document with the BusinessTypeID found in the previous step.
4. Checked the number of documents in the "Dover" Local Authority and removed all establishments within that area from the database. Verified the deletion by confirming the reduced number of documents in the collection.
5. Converted certain number values stored as strings to their appropriate numeric data types using update_many:
* Converted latitude and longitude fields to decimal numbers.
* Converted RatingValue field to integer numbers.

## Part 3: Exploratory Analysis
In this section, I performed an exploratory analysis of the database to answer specific questions posed by Eat Safe, Love. The analysis aims to help the magazine editors find desired locations to visit and avoid. Here's what I found:

1. Which establishments have a hygiene score equal to 20?
* Used the find method with a filter to select establishments with a hygiene score of 20.
* Displayed the count of documents, the first document using pprint, and converted the result to a Pandas DataFrame for further analysis.

2. Which establishments in London have a RatingValue greater than or equal to 4?
* Used the find method with a filter to select establishments in London with a RatingValue of 4 or higher.
* Displayed the count of documents, the first document using pprint, and converted the result to a Pandas DataFrame for further analysis.

3. What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?
* Calculated the latitude and longitude range for searching nearby establishments (within 0.01 degrees).
* Used the find method with filters for establishments with a RatingValue of 5 and coordinates within the defined range.
* Sorted the results by hygiene score in ascending order, limited the output to 5 documents, and converted the result to a Pandas DataFrame for further analysis.

4. How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten Local Authority areas.
* Used the aggregation method with a $match stage to filter establishments with a hygiene score of 0.
* Grouped the documents by Local Authority and counted the occurrences in each group.
* Sorted the results in descending order and printed the top ten Local Authority areas along with the count.

## Conclusion
By completing this analysis of the UK Food Standards Agency ratings data, I have provided valuable insights to the editors of Eat Safe, Love. The findings can guide their decisions on which establishments to feature in future articles, considering factors such as hygiene scores, ratings, and proximity to specific locations. The analysis demonstrates the potential of data-driven approaches in the food industry to ensure safety and quality for consumers.
