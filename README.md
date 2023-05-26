# nosql-challenge
Challenge 12: NoSQL databases using Mongo.db
<h2><b>Creating a NoSQL database and importing, transforming and querying data</b></h3>
<p>A fictional scenraio where the editors of a food magazine, Eat Safe, Love, wish to evaluate food hygiene ratings data provided by the UK Food Standards Agency to help their journalists and food critics decide where to focus future articles.</p>
<p><h3><b>This challenge has three parts:</b></h3</p>><ol>
  <li>Part 1: Create Database and Jupyter Notebook</li>
  <li>Part 2: Update the Database</li>
  <li>Part 3: Conduct an Exploratory Analysis</li></ol>
<p><h3>Part 1: Create Database and Jupyter Notebook</h3></p><ol>
  <li>The data is imported from a json file stored in the Resources folder (included in repository)</li>
  <li>The import command entered in the terminal is: <i>mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json</i></ol>
<p><h3>Part 2: Update and clean the Database</h3></p><ol>
  <li>Update the database with a new restaurant ('Penang Flavours') and update 'BusinessTypeID' field with a query retrieving the correct value.</li>
  <li>Remove all restaurants within the Dover LGA.</li>
  <li>Change the data type from sting to double in the geocode field for both longitude and latitude (see note below on why double is the best result in this use case)</li>
  <li>Change the data type in the 'RatingValue field' from string to integer. This involves first changing non-numeric strings to null values allowing the field to be updated to integer values (see note below over the issues that this causes in terms of the expected results set out in the marking scheme).</li></ol>
<p><h3>Part 3: Conduct an Exploratory Analysis</h3></p>
A number of tasks are requested within the exploratory analysis:<ol>
  <li>Which establishments have a hygiene score equal to 20?</li>
  <li>Which establishments in London have a RatingValue greater than or equal to 4? - Please see note below regarding this question.</li>
  <li>What are the top 5 establishments with a RatingValue of '5', sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?</li>
  <li>How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas.</li></ol>
  
<p><h3>Notes on Code</h3></p><ol>
<li>Change data type from String to Decimal for latitude. using "toDecimal" causes problems in Part 2 when applying operators to find other restaurants within a 0.1 degree range of Penang Flavours:</li><ul><li> https://stackoverflow.com/questions/41308044/mongodb-numberdecimal-unsupported-operand-types-for-decimal128-and-deci. To pass a Decimal128 instance in the Decimal constructor will however throw and error.</li><li>Double was used, and it gives enough precision to calculate restaurants within a certain proximty.</li>
<li>The instructions within the Module 12 Challenge on Bootcampspot instructs that we should: <i>Use update_many to convert RatingValue to integer numbers.</i> However when this is done, the result in the Data Analysis part of the challenge produces 33 results in reponse to the query returning the number of restaurants in City of London; however the marking scheme states that the correct result is 34.<blockquote><ul><i>Question 2: Which establishments in London have a RatingValue greater than or equal to 4? (12 points). . .
count_documents() is used to list the correct number of documents (answer: 34) (2 points)</i></li></ul></blockquote>
If the non-numeric strings are not removed by coercing to Null, the results include a resturant with a non-numeric value in the RatingValue field. A screenshot of the result printed out is included within the repository. The correct result would therefore appear to be 33.</li></ol>



