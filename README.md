# nosql-challenge
Challenge 12: NoSQL databases using Mongo.db
<h2><b>Creating a NoSQL database and inporting, transforming and querying data</b></h3>
<p>A fictional scenraio where the editors of a food magazine, Eat Safe, Love, wish to evaluate food hygiene ratings data provided by the UK Food Standards Agency to help their journalists and food critics decide where to focus future articles.</p>
<p><h3><b>This challenge has three parts:</b></h3</p>><ol>
  <li>Part 1: Create Database and Jupyter Notebook</li>
  <li>Part 2: Update the Database</li>
  <li>Part 3: Conduct an Exploratory Analysis</li></ol>
<h3>Part 1: Create Database and Jupyter Notebook</h3><ol>
  <li>The data is imported from a json file stored in the Resources folder (included in repository)</li>
  <li>The import command entered in the terminal is: <i>mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json</i></ol>
<p><h3>Part 2: Update the Database</h3></p><ol>
  <li>A new restaurant ('Penang Flavours') is entered into the database, together with updating the business number.</li>
  <li>

  

<h3><b>Notes on Code</b></h3>
For querying data type change in the data set-up part of the challenge, the 'print(type(result['geocode']['latitude']))' proved the simplest method, and returned only one field from a document, rather than the entire document. source: the Python Built-in Functions - type(): https://docs.python.org/3/library/functions.html#type<li>https://stackoverflow.com/questions/70602846/pymongo-get-mongodb-field-datatype></li>
<li>Change the data type from String to Decimal for latitude. Originally tried "toDecimal" but this caused problems in Part 2 when I needed to use operators to find other restaurants within a 0.1 degrees of Penang Flavours:</li><ul><li> https://stackoverflow.com/questions/41308044/mongodb-numberdecimal-unsupported-operand-types-for-decimal128-and-deci. To pass a Decimal128 instance in the Decimal constructor will however throw and error.</li><li>Double was used, and it gives enough precision to calculate restaurants within a certain proximty.</li>
<li>The instructions within the Module 12 Challenge on Bootcampspot instructs that we should <i>Use update_many to convert RatingValue to integer numbers.</i> However when this is done, the result in the Data Analysis part of the challenge produces 33 results in reponse to the query returning the number of restaurants in City of London; however the marking scheme states that the correct result is 34.<blockquote><ul><i><li>Question 2: Which establishments in London have a RatingValue greater than or equal to 4? (12 points)...</li>
<li>count_documents() is used to list the correct number of documents (answer: 34) (2 points)</i></li></ul></blockquote>
If the non-numeric strings are not removed by coercing to Null, the results include a resturant with a non-numeric value in the RatingValue field. A screenshot of the result printed out is included within the repository. The correct result would therefore appear to be 33.</li>



