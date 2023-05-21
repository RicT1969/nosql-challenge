# nosql-challenge
Challenge 12: NoSQL databases using Mongo.db
<h2><b>Creating a NoSQL database and inporting, transforming and querying data</b></h3>
<p>A fictional scenraio where the editors of a food magazine, Eat Safe, Love, wish to evaluate food hygiene ratings data provided by the UK Food Standards Agency to help their journalists and food critics decide where to focus future articles.</p>
<h3><b>This challenge has three parts:</b></h3><ol>
  <li>Part 1: Create Database and Jupyter Notebook</li>
  <li>Part 2: Update the Database</li>
  <li>Part 3: Conduct an Exploratory Analysis</li></ol>

<h3><b>Noteds on Code</b></h3>
  For querying data type change in teh data set-up part of the challenge, the 'print(type(result['geocode']['latitude']))' proved the simplest method, and returned only one field from a document, rather than the entire document. source: the Python Built-in Functions - type(): https://docs.python.org/3/library/functions.html#type<li>https://stackoverflow.com/questions/70602846/pymongo-get-mongodb-field-datatype></li>
<li>Change the data type from String to Decimal for latitude. Originally tried "toDecimal" but this caused problems in Part 2 when I needed to use operators to find other restaurants within a 0.1 degrees of Penang Flavours:</li><ul><li> https://stackoverflow.com/questions/41308044/mongodb-numberdecimal-unsupported-operand-types-for-decimal128-and-deci: states that "Decimal128 instances should be cast to standard Python decimals in order to operate them. But you should do that inside a context created by create_decimal128_context, from bson.decimal128, to ensure results can later be stored in the database". To pass a Decimal128 instance in the Decimal constructor will however throw and error.</li><li>On this basis Double was used, although its degree of precision is not as good. In this instance, it gives enough precision to calculate restaurants within a certain proximty.