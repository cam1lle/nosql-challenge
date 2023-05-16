# Food Ratings Database Analysis

This README.md file provides an overview of the steps I followed to complete the food ratings database analysis assignment.

__Part 1__: Database and Jupyter Notebook Set Up
To begin with the assignment, I followed the steps outlined below:

I opened the provided file NoSQL_setup_starter.ipynb in Jupyter Notebook.

Next, I imported the data from the establishments.json file into a MongoDB database named uk_food and a collection named establishments. I executed the following command in my Terminal to import the data:

mongoimport --db uk_food --collection establishments --file establishments.json

In the Jupyter Notebook, I imported the necessary libraries, namely PyMongo and Pretty Print (pprint), to work with the MongoDB database.

I created an instance of the Mongo Client to establish a connection with the MongoDB server.

To ensure that the database and data were loaded correctly, I performed the following steps:

I listed the databases in MongoDB and confirmed that uk_food was listed.
I listed the collections in the uk_food database and verified that establishments was present.
I retrieved and displayed one document from the establishments collection using the find_one method and pprint to visualize the data.
Finally, I assigned the establishments collection to a variable for further use.

__Part 2__: Update the Database
In this part, I made the requested modifications to the establishments collection. Here's how I completed this section:

I continued working with the NoSQL_setup_starter.ipynb notebook.

An exciting new halal restaurant, "Penang Flavours," opened in Greenwich but had not been rated yet. The magazine editors requested that I include it in the analysis. I added the provided information as a new document in the establishments collection.

I needed to find the BusinessTypeID for the "Restaurant/Cafe/Canteen" category and return only the BusinessTypeID and BusinessType fields.

Once I identified the BusinessTypeID, I updated the newly added restaurant document with the corresponding BusinessTypeID value.

The magazine editors indicated that they were not interested in any establishments in Dover. Therefore, I checked the number of documents in the collection that contained the Dover Local Authority. I then removed all establishments within the Dover Local Authority from the database and confirmed the deletion by checking the remaining number of documents.

Some of the number values in the collection were stored as strings instead of actual numbers. To address this, I used the update_many method to convert the latitude and longitude fields to decimal numbers. Additionally, I converted the RatingValue field to integer numbers.

__Part 3__: Exploratory Analysis
In this part, I explored the database and answered specific questions posed by the magazine editors. Here's how I approached the analysis:

Using the NoSQL_analysis_starter.ipynb notebook, I focused on answering the provided questions, keeping in mind the following information about the dataset:

The RatingValue field represents the overall rating given by the Food Authority, ranging from 1 to 5, with higher values indicating better ratings. Note that this field can also contain non-numeric values such as 'Pass'.
The scores for Hygiene, Structural, and ConfidenceInManagement work in reverse, where higher values indicate worse performance in those areas.
For each question, I followed these steps:

Used count_documents to display the number of matching
documents.

Displayed the first document in the results using pprint.

Converted the result to a Pandas DataFrame, printed the number of rows in the DataFrame, and displayed the first 10 rows.

I identified the establishments with a hygiene score equal to 20.

I found the establishments in London with a RatingValue greater than or equal to 4, taking into account that the London Local Authority has a longer name, requiring the use of $regex in the search.

To determine the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score and closest to the new restaurant, "Penang Flavours," I compared the geocode values and searched within a 0.01-degree radius on either side of the latitude and longitude.

I calculated the number of establishments in each Local Authority area that have a hygiene score of 0. The results were sorted from highest to lowest, and I printed out the top ten Local Authority areas.

The analysis provided valuable insights into the food ratings data, helping the magazine editors identify establishments of interest and make informed decisions for future articles.

Please note that all the steps and analysis described above were completed successfully, contributing to the completion of the food ratings database analysis assignment.