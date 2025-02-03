# NoSQL Challenge

---

## Required Files

[Resources](https://static.bc-edx.com/data/dl-1-2/m12/lms/starter/Starter_Code.zip)

[Setup Code]([Uploading NoSQL_setup_starter.ipynb…]()

[Starter Code]([Uploading NoSQL_analysis_starter.ipynb…]()


## Instructions
The UK Food Standards Agency evaluates various establishments across the United Kingdom and provides food hygiene ratings. You have been contracted by the editors of a food magazine, *Eat Safe, Love*, to analyze some of this data to assist their journalists and food critics in determining where to focus future articles.

---

### Part 1: Database and Jupyter Notebook Set Up

Use `NoSQL_setup_starter.ipynb` for this section of the challenge.

1. **Import the Data**  
   Import the data from the `establishments.json` file through your Terminal. Name the database `uk_food` and the collection `establishments`.  
   Copy and paste the text used to import the data into a markdown cell in your notebook.

2. **Import Libraries**  
   Within your notebook, import the necessary libraries:
   - `PyMongo`
   - `Pretty Print (pprint)`

3. **Create Mongo Client Instance**  
   Create an instance of the Mongo Client to interact with MongoDB.

4. **Verify Database and Collection**  
   Confirm that the `uk_food` database is created and the data is loaded properly by:
   - Listing the databases in MongoDB to ensure `uk_food` is present.
   - Listing the collections in the `uk_food` database to confirm the `establishments` collection exists.

5. **Display One Document**  
   Use `find_one` to retrieve one document from the `establishments` collection and display it with `pprint`.

6. **Assign Collection to Variable**  
   Assign the `establishments` collection to a variable for further use in the analysis.

---

### Part 2: Update the Database

Use `NoSQL_setup_starter.ipynb` for this section of the challenge.

1. **Add New Restaurant**  
   A new halal restaurant in Greenwich, which has not been rated yet, needs to be added to the database. Include the following details for the restaurant:

   ![Image](https://github.com/user-attachments/assets/ef895df6-de1d-46bc-8dcf-38f496081f66)

2. **Find BusinessTypeID for "Restaurant/Cafe/Canteen"**  
   Find the `BusinessTypeID` for "Restaurant/Cafe/Canteen" and return only the `BusinessTypeID` and `BusinessType` fields.

3. **Update the New Restaurant**  
   Update the newly added restaurant with the `BusinessTypeID` you found in the previous step.

4. **Remove Establishments in Dover**  
   The magazine is not interested in establishments located in Dover.  
   - First, check how many documents contain the Dover Local Authority.
   - Then, remove the establishments located in Dover from the database.
   - Check the number of documents to confirm the deletions.

5. **Update Latitude, Longitude, and Rating Values**  
   Some values for latitude, longitude, and RatingValue are stored as strings when they should be stored as numbers.  
   - Use `update_many` to convert latitude and longitude to decimal numbers.
   - Use `update_many` to convert `RatingValue` to integers.

---

### Part 3: Exploratory Analysis

Use `NoSQL_analysis_starter.ipynb` for this section of the challenge.

When performing exploratory analysis, note that:
- `RatingValue` refers to the overall rating from the Food Authority and ranges from 1-5, with higher values indicating better ratings.
- The scores for Hygiene, Structural, and ConfidenceInManagement work in reverse: higher values indicate worse performance in these areas.
- Non-numeric values such as "Pass" in `RatingValue` will be coerced to nulls before conversion.

#### Analysis Answers

1. **Which establishments have a hygiene score equal to 20?**
   - Use `count_documents` to display the number of documents in the result.
   - Display the first document in the result using `pprint`.
   - Convert the result to a Pandas DataFrame, print the number of rows, and display the first 10 rows.

2. **Which establishments in London have a `RatingValue` greater than or equal to 4?**
   - The London Local Authority has a longer name than just "London," so you will need to use `$regex` for your search.
   
3. **Top 5 establishments with a `RatingValue` of 5, sorted by lowest hygiene score, nearest to the new restaurant "Penang Flavours":**
   - You will need to compare the latitude and longitude of the establishments to find the nearest ones. 
   - Consider establishments within 0.01 degrees of latitude and longitude on either side.

4. **How many establishments in each Local Authority area have a hygiene score of 0?**
   - Sort the results from highest to lowest.
   - Print the top ten local authority areas.

   Hint: Use aggregation methods to answer this question.

   The first 5 rows of your resulting DataFrame should look like:

   ![Image](https://github.com/user-attachments/assets/b3de9e1b-43d1-4abd-9b9b-8c15f5019c11)



---
