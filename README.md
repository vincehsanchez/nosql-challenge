# nosql-challenge

The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. 

You've been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.

### Part 1: Database and Jupyter Notebook Set Up

**NOTE:**
Use NoSQL_setup_starter.ipynb for this section of the challenge.

1. Import the data provided in the establishments.json file from your Terminal. 
2. Name the database uk_food and the collection establishments. Copy the text you used to import your data from your Terminal to a markdown cell in your notebook.
3. Within your notebook, import the libraries you need:
    - PyMongo
    - Pretty Print (pprint).
4. Create an instance of the Mongo Client.
5. Confirm that you created the database and loaded the data properly:
6. List the databases you have in MongoDB. Confirm that uk_food is listed.
7. List the collection(s) in the database to ensure that establishments is there.
8. Find and display one document in the establishments collection using find_one and display with pprint.
9. Assign the establishments collection to a variable to prepare the collection for use.

### Part 2: Update the Database

The magazine editors have some requested modifications for the database before you can perform any queries or analysis for them. 

An exciting new halal restaurant just opened in Greenwich, but hasn't been rated yet. The magazine has asked you to include it in your analysis.

**NOTE:**
Use NoSQL_setup_starter.ipynb for this section of the challenge.

Make the following changes to the establishments collection:
1. Add new restaurant to database.
2. Find the BusinessTypeID for "Restaurant/Cafe/Canteen" and return only the BusinessTypeID and BusinessType fields.
3. Update the new restaurant with the BusinessTypeID you found.
    
The magazine is not interested in any establishments in Dover, so check how many documents contain the Dover Local Authority.
1. Remove any establishments within the Dover Local Authority from the database
2. Check the number of documents to ensure they were deleted.
3. Some of the number values are stored as strings, when they should be stored as numbers.
4. Use update_many to convert latitude and longitude to decimal numbers.
5. Use update_many to convert RatingValue to integer numbers.

### Part 3: Exploratory Analysis
Eat Safe, Love has specific questions they want you to answer, which will help them find the locations they wish to visit and avoid.

Use the following questions to explore the database, and find the answers, so you can provide them to the magazine editors.

1. Which establishments have a hygiene score equal to 20?
2. Which establishments in London have a RatingValue greater than or equal to 4?
3. What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?
4. How many establishments in each Local Authority area have a hygiene score of 0?
Sort the results from highest to lowest, and print out the top ten local authority areas.

Unless otherwise stated, for each question:
- Use count_documents to display the number of documents contained in the result.
- Display the first document in the results using pprint.
- Convert the result to a Pandas DataFrame, print the number of rows in the DataFrame, and display the first 10 rows.

**NOTE:**
- Use NoSQL_analysis_starter.ipynb for this section of the challenge.
- RatingValue refers to the overall rating decided by the Food Authority and ranges from 1-5.
- The higher the value, the better the rating.
- This field also includes non-numeric values such as 'Pass', where 'Pass' means that the establishment passed their inspection but isn't given a number rating.
    - We will coerce non-numeric values to nulls during the database setup before converting ratings to integers.
- The scores for Hygiene, Structural, and ConfidenceInManagement work in reverse.
    - This means, the higher the value, the worse the establishment is in these areas.
