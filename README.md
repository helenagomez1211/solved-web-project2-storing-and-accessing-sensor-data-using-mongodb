Download Link: https://assignmentchef.com/product/solved-web-project2-storing-and-accessing-sensor-data-using-mongodb
<br>
The aims of this project are as follows:

<ul>

 <li>To give you more experience with JavaScript programming.</li>

 <li>To expose you to mongodb.</li>

 <li>To make you comfortable using nodejs packages and module system.</li>

</ul>

<h1>1.2        Requirements</h1>

You must push a submit/prj2-sol directory to your github repository such that typing npm ci within that directory is su cient to run the project using ./index.js.

You are being provided with an index.js which provides the required commandline behavior. What you speci cally need to do is add code to the provided sensors.js source le as per the requirements in that le.

The API is extremely similar to that for your previous project. The di erences include:

<ul>

 <li>The Sensors class must provide persistent storage by using a <a href="https://www.mongodb.com/">mongodb </a></li>

 <li>An instance of the Sensors class is created externally by calling an async newSensors() factory method. This is for reasons discussed in class.</li>

 <li>All application errors are reported using an array of AppError objects. The provided AppError class simply wraps an error code and message; the code will make it easy to classify errors in future projects.</li>

</ul>

The behavior of the program is illustrated in this annotated log.

<h1>1.3        Provided Files</h1>

The prj2-sol directory contains a start for your project. It contains the following les:

sensors.js This skeleton le constitutes the guts of your project. You will need to esh out the skeleton, adding code as per the documentation. You should feel free to add any auxiliary function or method de nitions as required.

The provided code does most (not all) the validations necessary for this project.

index.js This le provides the complete command-line behavior which is required by your program. It requires sensors.js. You must not modify this le; this ensures that your Sensors class meets its speci cations and facilitates automated testing by testing only the Sensors API.

app-error.js A trival class for application errors.

validate.js Validation code from the previous project. Note that it provides generic validation based on types for input parameters. More validation will be necessary, especially for checking that a parameter speci es some other object via its id.

README A README le which must be submitted along with your project. It contains an initial header which you must complete (replace the dummy entries with your name, B-number and email address at which you would like to receive project-related email). After the header you may include any content which you would like read during the grading of your project.

Additionally, the course data directory contains sensor data les. It’s content is identical to the previous project except that the error data les have been enhanced with objects which shows the errors resulting from references to nonexisting objects.

<h1>1.4        MongoDB</h1>

<a href="https://docs.mongodb.com/manual/">MongoDB</a> is a popular nosql database. It allows storage of collections of documents to be accessed by a primary key named _id.

In terms of JavaScript, mongodb documents correspond to arbitrarily nested JavaScript Objects having a top-level _id property which is used as a primary key. If an object does not have an _id property, then one will be created with a unique value assigned by mongodb.

<ul>

 <li>MongoDB provides a basic repertoire of <a href="https://docs.mongodb.com/manual/crud/">CRUD Operations</a><a href="https://docs.mongodb.com/manual/crud/">.</a></li>

 <li>All asynchronous mongo library functions can be called directly using await.</li>

 <li>It is important to ensure that all database connections are closed. Otherwise your program will not exit gracefully.</li>

</ul>

You can play with mongo by starting up a <a href="https://docs.mongodb.com/manual/mongo/">mongo shell</a><a href="https://docs.mongodb.com/manual/mongo/">:</a>

$ $ mongo

MongoDB shell version v3.6.3 connecting to: mongodb://127.0.0.1:27017 MongoDB server version: 3.6.3

Server has startup warnings: …

&gt; help

db.help()                                                      help on db methods

…

exit                                                                  quit the mongo shell

&gt;

Since mongodb is available for di erent languages, make sure that you are looking at the <a href="https://mongodb.github.io/node-mongodb-native/3.3/quick-start/quick-start/">nodejs documentation</a><a href="https://mongodb.github.io/node-mongodb-native/3.3/quick-start/quick-start/">.</a>

<ul>

 <li>You can get a connection to a mongodb server using the mongo client’s asynchronous <a href="https://mongodb.github.io/node-mongodb-native/3.3/api/MongoClient.html#.connect">connect()</a></li>

 <li>Once you have a connection to a server, you can get to a speci c database using the synchronous <a href="https://mongodb.github.io/node-mongodb-native/3.3/api/MongoClient.html#db">db()</a></li>

 <li>From a database, you can get to a speci c collection using the synchronous <a href="https://mongodb.github.io/node-mongodb-native/3.3/api/Db.html#collection">collection()</a></li>

 <li>Given a collection, you can asynchronously insert into it using the <a href="https://mongodb.github.io/node-mongodb-native/3.3/api/Collection.html#insertOne">insert*() </a> However, the code for using insert*() to do replacements can get complicated. An easier alternative may be to use the asynchronous <a href="https://mongodb.github.io/node-mongodb-native/3.3/api/Collection.html#replaceOne">replaceOne()</a> method with the <a href="https://docs.mongodb.com/manual/reference/method/db.collection.replaceOne/">upsert</a> option.</li>

 <li>Given a collection, you can asynchronously <a href="https://mongodb.github.io/node-mongodb-native/3.3/api/Collection.html#find">nd()</a> a cursor which meets the criteria speci ed by a query to find(). The query can be used to lter the collection; speci cally, if the lter speci es an _id, then the cursor returned by the find() should contain at most one result.</li>

 <li>Given a cursor, you can modify it using the synchronous <a href="https://mongodb.github.io/node-mongodb-native/3.3/api/Cursor.html#sort">sort(),</a> <a href="https://mongodb.github.io/node-mongodb-native/3.3/api/Cursor.html#skip">skip()</a> and <a href="https://mongodb.github.io/node-mongodb-native/3.3/api/Cursor.html#limit">limit()</a></li>

 <li>Given a cursor, you can get all its results as an array using the asynchronous <a href="https://mongodb.github.io/node-mongodb-native/3.3/api/Cursor.html#toArray">toArray()</a></li>

</ul>

<h1>1.5       Hints</h1>

The following steps are not prescriptive in that you may choose to ignore them as long as you meet all project requirements.

<ol>

 <li>Read the project requirements thoroughly. Look at the sample log to make sure you understand the necessary behavior. Review the material covered in class including the user-store</li>

 <li>Look into debugging methods for your project. Possibilities include:

  <ul>

   <li>Logging debugging information onto the terminal using <a href="https://developer.mozilla.org/en-US/docs/Web/API/Console/log">log() </a>or <a href="https://developer.mozilla.org/en-US/docs/Web/API/Console/error">console.error().</a></li>

   <li>Use the chrome debugger as outlined in this</li>

  </ul></li>

</ol>

The couple of minutes spent looking at this link and setting up chrome as your debugger for this project will be more than repaid in the time saved adding and removing console.log() statements to your code.

<ol start="3">

 <li>Consider how you can use mongo to implement this project. to access its sensor type and readings easily. Try to use mongo’s facilities as much as possible; for example, instead of writing code for ltering, design your database objects such that you can use the ltering capabilities of mongo’s <a href="https://mongodb.github.io/node-mongodb-native/3.3/api/Collection.html#find">nd()</a> method; use the cursor modi cation methods like <a href="https://mongodb.github.io/node-mongodb-native/3.3/api/Cursor.html#skip">skip()</a> and <a href="https://mongodb.github.io/node-mongodb-native/3.3/api/Cursor.html#limit">limit()</a></li>

</ol>

to implement paging within results.

Since opening a connection to a database is an expensive operation, it is common to open up a connection at the start of a program and hang on to that connection for the duration of the program. It is also important to remember to close the connection before termination of the program.

[Note that the command-line program for this project performs only a single command for each program run. Nevertheless, the API provided for Sensors allows for multiple operations for each instance; hence you should associate the database connection with the instance of Sensors.]

<ol start="4">

 <li>Start your project by creating a work/prj2-sol directory in the i444 or i544 directory corresponding to your github repository. Change into the newly created prj2-sol directory and initialize your project by running npm init -y. This will create a package.json le; this le should be committed to your repository.</li>

 <li>Install the mongodb client library using npm install mongodb. It will install the library and its dependencies into a node_modules directory created within your current directory. It will also create a package-¬ json which must be committed into your git repository.</li>

</ol>

The created node_modules directory should not be committed to git. You can ensure that it will not be committed by simply mentioning it in a .gitignore le. You should have already taken care of this if you followed the directions provided when setting up github. If you have not done so, please add a line containing simply node_modules to a .gitignore le at the top-level of your i444 or i544 github project.

<ol start="6">

 <li>Copy the provided les into your project directory:</li>

</ol>

$ cp -pr $HOME/cs544/projects/prj2/prj2-sol/* .

This should copy in the README template, the index.js, the sensors.js skeleton le and the utility les app-error.js and validate.js into your project directory.

<ol start="7">

 <li>You should be able to run the project but all commands will return without any results until you replace the @TODO sections with suitable code.</li>

</ol>

The provided code does have su           cient functionality to get a usage message:

$ ./index.js

usage: index.js MONGO_DB_URL CMD [ARGS…] Command CMD can be add sensor-type|sensor|sensor-data NAME=VALUE… clear clear all sensor data

find              sensor-type|sensor|sensor-data [NAME=VALUE…]

help output this message load sensor-type|sensor|sensor-data JSON_FILE…

or do some simple validations:

$ ./index.js GARBAGE_URL clear _id=1 sorry; clear does not accept any arguments

$ ./index.js GARBAGE_URL find sensor-type _id=1 RESERVED: the _id parameter is reserved for internal use only

<ol start="8">

 <li>Replace the XXX entries in the README template.</li>

 <li>Commit your project to github:</li>

</ol>

$ git add .

$ git commit -a -m ’started prj2’

<ol start="10">

 <li>Open the copy of the sensors.js le in your project directory. It contains

  <ul>

   <li>A strict declaration followed by initial imports. The local imports include the AppError wrapper class as well as a validate() module which contains the generic validation code from the previous project.</li>

   <li>A skeleton Sensors class de nition with speci cation comments and @TODO comments. The speci cation comments specify the behavior of the methods you need to complete.</li>

   <li>An assignment of the Sensors class to module.exports. This makes Sensors the only declarations available outside the sensors¬ .js le; all other declarations are local to the le.</li>

   <li>Options that you should use when creating a connection to a mongo db.</li>

   <li>A trivial utility function.</li>

  </ul></li>

</ol>

Some points worth making about the provided code:

<ul>

 <li>All the methods have been declared async. This allows you to await asynchronous calls to mongo library functions.</li>

 <li>For error handling, the convention used is that all user errors should be thrown as lists of AppError (for example, see the throw’s within the validate module). If you need to throw your own errors, be sure to wrap them into AppError objects in a list. Wrap in the list even for a single error:</li>

</ul>

if (/* no sensor-type for speci ed sensor model */) {

const err = ‘no model ${model} sensor type‘;

throw [ new AppError(’X_ID’, err) ];

}

The two levels of wrapping achieves the following:

Wrapping in the AppError allows an error object to contain a code which can be used subsequently to classify the error.

Wrapping the errors into a list allows reporting multiple errors in a single API call. It also allows the calling code to distinguish between exceptions caused by intentional error reporting and those caused inadvertently; the former can be reported as simple error messages whereas the latter will be reported using a full stack trace. This makes it much easier to debug your code when you get unintentional exceptions.

<ol start="11">

 <li>Start by implementing the factory method for newSensors().

  <ul>

   <li>Validate the parameters to the method. The mongoDbUrl must be a valid URL of the form mongodb://HOST:PORT/DB. If invalid, return a suitable error.</li>

   <li>If the parameters are valid, connect to the database (note that you will need to split mongoDbUrl into the base part and the database name).</li>

   <li>Finally, synchronously call the constructor(). The constructor should cache the database client connection in the instance and set up instance variables for the database collections you are using.</li>

  </ul></li>

</ol>

[An instance of a Sensors should contain a database connection, but obtaining a database connection is an asynchronous operation. Since it is impossible to have an <a href="https://stackoverflow.com/questions/43431550/async-await-class-constructor">asynchronous constructor</a><a href="https://stackoverflow.com/questions/43431550/async-await-class-constructor">,</a> an async factory method provides a workaround].

<ol start="12">

 <li>Implement the close() method for Sensors. You simply need to await a close() on your database client.</li>

 <li>The code for adding a sensor-type, sensor or sensor-data is likely to be very similar. Factor out this commonality into a “private” method (there are no “private” methods in JavaScript; a common convention is to indicate that a method is intended to be private by having its name start with a</li>

</ol>

_.).

<ol start="14">

 <li>As for the add*() methods, many of the find*() methods will be very similar. Once again, factor out this commonality into a “private” method.</li>

 <li>Implement the add*() methods as wrappers which simply call the private methods but also take care of any validations not handled by the validate() function.</li>

 <li>Implement the findSensorType() and findSensor() methods. They should largely be wrappers calling your private methods.</li>

 <li>Implement the findSensorData() method. It too will call your private methods, but because of the non-standard use of timestamp’s for paging through the data, this function is likely to contain non-trivial logic.</li>

 <li>Iterate until you meet all requirements.</li>

</ol>