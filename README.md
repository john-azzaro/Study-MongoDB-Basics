# MongoDB Basics Study

<br>

## What is MongoDB Basics Study?
The "MongoDB Basics Study" explores the basic functionality of MongoDB and operation in a local development enviroment including installation, interactions with the MongoDB shell, etc.

<br>

Here's an overview of what this study covers:

* [What is MongoDB?](#)
* [How do you install MongoDB?](#)
* [How do you use the interactive Mongo shell?](#)
* [How do you exit Mongo shell and Mongod?](#)
* [How do you navigate Mongo Shell?](#)
* [How do you exit Mongo shell and Mongod?](#)
* [What does the structure of MongoDB look like?](#)
* [How do you create a document in the MongoDB local environment?](#)


<br>

## What is MongoDB?
MongoDB is a popular, open-source, schema-less NoSQL document database that uses a document-oriented data model and non-structured query language (NoSQL).

Unlike data stored to memory (which will be lost when the server restartes) and SQL relational databases (which relies on rows and columns), a MongoDB **database**, which is essentially the container for data, is built on *collections* of *documents* which are versatile data models that allow you to combine and store data of many types. 

**Collections** are a *collection* of documents (and are analogous to *tables* in relational databases). Collections hold instance of a signle type of document. For example, a collection
of sports cars (e.g. Ferarri).  

**Documents** hold instances of that collection.  For example, a collection of of Ferrari sports cars would have different documents of those sports cars (e.g. Fararri 458, Ferrari 488, Ferrari Superfast, etc.). 

Some additional features to consider:
* A document contains *key/value pairs* allowing documents to have fields and structures in *BSON* (i.e. binary style of JSON) document formats. 
* Mongo accepts stings, integers, floating point decimals, booleans, null, arrays, objects, time stamps, and object ids as value types. 
* Mongo databases feature *flexible schemas*, which means that all documents in a collection do NOT need to have the same structure.
* Mongo has a number of collection methods that can create, read, update, and delete documents.  


<br>

## How do you install MongoDB?
Installing MongoDB is a little tricky in that you need to do a few things like editing path variables, using command prompt,
and adding a default storage file for your Mongo databases on your local machine.  Follow the steps below to get started with
MongoDB and take special note of some of the observations and issues you might encounter and how to resolve them.


#### Step 1: Download MongoDB from https://www.mongodb.com/download-center/community :
> *note: make sure you download the community*

#### Step 2: Once the download is complete, install on your local machine:
> *note: DO NOT INSTALL MONGODB COMPASS at this time.  A few issues made it difficult to install... install compass AFTER installation.* 

#### Step 3: Navigate to the installation folder, find "mongod" and copy the directory
> *note: Your installation file directory might be different, but it should look like this: C:\Program Files\MongoDB\Server\4.0\bin*
> *factual note: "mongod" is "mongo daemon" which is the mongoDB server*

#### Step 4: In your search bar, look for "advanced system settings", select "enviroment variables", edit the PATH variable by adding the previous path.
> *note: make sure you put the entire path (i.e. "C:\Program Files\MongoDB\Server\4.0\bin" ) in so that it works correctly*

#### Step 5: Install MongoDB Compass to use the database GUI (graphical user interface).
> *note: make sure you install the community verison*

#### Step 6: In command prompt, run "mongod" for the first time and (if needed) create a "db" directory for your future data
* When you run "mongod" for the first time you may get an issue that says:
```
        exception in initandlisten: NonExitentPath: Data directory C:\data\db not found, terminating
```
* This isnt something to be worried about, it simply means that the default folder where you store your mongoDB data hasnt been made yet
* To make your data folder, write the following in Gitbash
```
        md c:\data\db
```
* With this done, you should have successfully setup your Mongo Database!

<br>


## How do you use the interactive Mongo shell?
The mongo shell interface allows us to create databases, documents, update, delete, manage collections etc. allowsWhen you use the interactive mongo shell, you are essentially interfacing with your database.  Although much more time will be spent interacting with Mongo through an ORM layer such as *mongoose*, working with Mongo directly is very useful.

**Step 1: First, run "mongod" in command prompt** 
> *note: once you run "mongod", you wont need to use the command prompt window much because we will be using Gitbash to interface with the database, so you can set it aside*
```
        mongod                            
```
<br>

**Step 2: Second, run "mongo" in Gitbash to start using the interactive mongo shell**
* In Gitbash, write:
```
        mongo
```
* When you run mongo, you should see something like this:
```
        $ mongo
        MongoDB shell version v4.0.5
        connecting to: mongodb://127.0.0.1:27017/?gssapiServiceName=mongodb
        Implicit session: session { "id" : UUID("fdfdb4ce-ecfc-4fd1-b426-3887a1ac7fd3") }
        MongoDB server version: 4.0.5
```
* Now you can navigate your mongo collections!
<br>

## How do you exit Mongo shell and Mongod?
* To exit mongo shell in gitbash, write:
```
        quit()
```
* To exit mongod in command prompt, press:
```
        ctrl-c
```
<br>

## How do you navigate Mongo Shell?

| **What it does:**                                 | **Command in mongo shell:**                             |
| ------------------------------------------------- | ----------------------------------------------------------------------|
|                                                   |   *Note: myDatabase > myCollection > myDocument*                                |
|      **BASIC NAVIGATION**                         |                                                                |
|                                                   |                                                                |
|      To find your current location                |   ```db```                                                        |
|      To show current databases                    |   ```show dbs```                                            |
|      To use (and/or create) a database            |   ```use myDatabase```                                        |
|                                                   |                                                                |
|      **SHOW/CREATE DATABASES/COLLECTIONS**        |                                                                |
|                                                   |                                                                |
|      To show collections in database              |   ```show collections```                                      |
|      To show all collections by name              |       ```db.getCollectionNames()```                              |
|      To create a new collection                   |   ```db.createCollection('myCollection');```          |
|                                                   |                                                                |
|      **CREATE DATA**                              |                                                                                   |
|                                                   |                                                                                   |
|         To find a single document                 |     ``` db.myCollection.findOne();```                                          |
|         To insert documents                       |      ``` <variable-to-insert> + db.myCollection.insert(variable);```           |
|         To insert a document                      |      ``` <variable-to-insert> + db.myCollection.insertOne(variable);```           |
|         To insert array of documents              |      ``` <variable/array> + db.myCollection.insertMany(variable);```           |
|         To insert a document                      |      ``` <variable/object> + db.<myCollection.insertOne(variable);```           |
|                                                   |                                                                                   |
|      **READ DATA**                                |                                                                |
|                                                   |                                                                |
|        To return ALL documents                    |    ``` db.myCollection.find()```                               |
|        To return query                            |    ```db.restaurants.find({lastName: "Smith"}, {isMember: true,}); ```                  |
|        To return query with arrangement           |    ```.find({lastName: "Smith"}, {isMember: true,}.limit(3))```             |
|                                                   |                                                                |
|      **UPDATE DATA**                              |                                                                |
|                                                   |                                                                |
|        To update a document                       |    ```db.restaurants.updateOne({_id: objectId}, {$set: {name: "Joe"}});```                                                            |
|        To replace a document                       |    ```db.restaurants.replaceOne({_id: objectId}, {$set: {name: "Joe"}});```                                                            |
|                                                   |                                                                |
|      **DELETE DATA**                              |                                                                |
|                                                   |                                                                |
|      To delete database                           |   ```db.dropDatabase();```                                         |
|                                                   |                                                                |
|                                                   |                                                                |
|                                                   |                                                                |
|                                                   |                                                                |
|                                                   |                                                                |
|      Import data                                  |   ```mongoimport -d <db-name> -c <collection-name> --drop -f ~/data.json```         |





<br>

## What does the structure of MongoDB look like?
To get a good idea of the general structure of MongoDB, install MongoDB Compass.  MongoDB Compass is a simple GUI that allows users to explore, insert, modify, and delete from your databases visually as well as run ad hoc queries.  Inside MongoDB compass, you can see all of your **databases**.  For example, you would see something like the ```testDB``` database.  
```     
        > admin
        > config
        > local
        > testDB
```
Inside that database, you would see a list of **collections** with additional information, such as: 
```
    Collection Name    Docs    Avg. Doc Size   Total Doc Size    Num. Indexes    Total Index Size    Properties
    _______________    _____   _____________   ______________    ____________    ________________    __________
        books          3,950      451.2 B         1.8 MB               1             45.1 KB          
```
And for each **document** in that collection, you will have a list of key/value pairs.  In the example below, you have a JSON object for an cookbook, with a variety of properties as well as a unique identifier ```"_id":"59074c7c057aaffaafb0da64" ``` for this particular document.  
```
        {"_id":"59074c7c057aaffaafb0da64",
        "Author": {"firstName": "Joe", "lastName": "Smith"},                      
        "genre":"fiction",
        "uisinec":"Italian",
        "reviews": [{"italian news network": "Wow, this bread book is fantastic"}]     
        "name":"Making Italian Bread the Easy Way",
        "book_id":"40365784"}
```

<br>

## How do you import data into Mongo?
Suppose you have a collection you want to import into MongoDB.  To do this, what you would need to write the following command in Gitbash:
```
mongoimport --db <database-name> --collection <collection-name> --drop --file ~/<file-location-route>
```
Breaking down the previous mongoimport command, it does the following:
* ```mongoimport ``` instructs mongo to import the database to mongo.
* ``` --db <database-name> ``` imports the data to a database name X, like "users" or "books".
* ```--collection <collection-name> ``` imports the data to collection in database named X, like "cookbooks".
* ``` --drop ``` is a flag that says that if there is an exisiting collection of the same name, to drop it.
* ``` --file ~/<file-location-route>``` is the location of the of the file to be imported (i.e. /Desktop/cookbooks.json).

<br>

## How do you CREATE a document in the MongoDB local environment?
To create a document in your local enviroment, you need to a variable (using the *var* keyword) with an object as the value and the mongo create command:

```
        db.restaurants.insert(myRestaurant);
```

Note that there are a few ways to insert documents to your database.
1. To inser documents (one or many) to your database, use ``` .insert``` method.
2. To insert ONE documents to your database, you would use the ``` .insertOne``` method.
3. To insert MANY documents (inside an array) to your database, you would use the ``` .insertMany ``` method.

In the following, we are creating a single document named "burgerRestaurant" from a function expression given beforehand.
```
        var burgerRestaurant = {
          address: {},
          borough: "Manhattan",
          cuisine: "American",
          grades: [],
          name: "Burger Nook",
          restaurant_id: "373737373737373737"
        }
        db.restaurants.insertOne(burgerRestaurant);            
```
If you successfully submit this document, you will receieve the following output:
```
        {
                "acknowledged" : true,                                    // Successfully added to database
                "insertedId" : ObjectId("5d7d14666b1bd9be37a12199")       // unique id provided by Mongo
        }      
```
Note that the ``` insertedId``` is the unique identifier code mongo creates for each document you add.  Although you can create your own id code, it is best that you let Mongo handle that for you.  

<br>

## How do you READ a document from an existing database?
When you attempt to read a document from a database, you need consider 2 things: *querying* and *arranging*.

#### Querying with .find
First, you need to **query** so as to find the relevant documents (i.e. results that match specific properties in your document's key/value pairs).  For example, we want to find restaurants in the borough of Soho, etc.  To query, you can use the ``` .find ``` method.  *Find* can be called with TWO optional parameters: a *query object* that matches the matching criteria and a *projection object* that controls what properties are returned from each document.  Take the following query:

```
        db.restaurants.find({borough: "Manhattan"}, {name: 1,});
```
This says that for all document in the restraurants collection, find only those with a "borough" property eqal to the string value "Manhatten" and for those documents that do match, just return the name of the restaurant *(note that ``` 1``` denotes its inclusion in the search).*  

The output would look something like this:
```
        db.restaurants.find({borough: "Manhattan"}, {name: 1});
        { "_id" : ObjectId("59074c7c057aaffaafb0da75"), "name" : "Nanni Restaurant" }
        { "_id" : ObjectId("59074c7c057aaffaafb0da88"), "name" : "The Riviera Cafe" }
        { "_id" : ObjectId("59074c7c057aaffaafb0da6d"), "name" : "Hop Kee Restaurant" }
        { "_id" : ObjectId("59074c7c057aaffaafb0daa2"), "name" : "Jg Melon Restaurant" }
        { "_id" : ObjectId("59074c7c057aaffaafb0daa8"), "name" : "Jackson Hole" }
        { "_id" : ObjectId("59074c7c057aaffaafb0da60"), "name" : "Joe Allen Restaurant" }
        { "_id" : ObjectId("59074c7c057aaffaafb0dabd"), "name" : "Fiorellos" }
        { "_id" : ObjectId("59074c7c057aaffaafb0dad0"), "name" : "Da Silvano Restaurant" }
        { "_id" : ObjectId("59074c7c057aaffaafb0daca"), "name" : "Oyster Bar" }
```

#### Arranging results
When you **arrange** your results, you are simply deciding what data you want to be returned back to you, whether that be ordering, filtering, etc. To arrange results, you can chain additional methods like ```.sort```, ```.limit```.  So for example, if you wanted to limit your results to the 3 and sort the results alphabetically, you would query as follows:
```
        db.restaurants.find({borough: "Manhattan"}, {name: 1,}).sort({name: 1}).limit(3);
```
The output would then give you the top alphabetically sorted names, which in this case would be numerical!
```
        { "_id" : ObjectId("59074c7c057aaffaafb0f8d8"), "name" : "12 Street Ale House" }
        { "_id" : ObjectId("59074c7c057aaffaafb1063a"), "name" : "137 Bar & Grill" }
        { "_id" : ObjectId("59074c7c057aaffaafb0f22e"), "name" : "169 Bar" }
```

<br>

## How do you UPDATE a document?
Updating a document in Mongo can either be done by updating one of the properties of a document *or* the entire document itself.  To update a document (i.e. replace one set of information with an another *updated* set of infromation), you need to:
1. Specify the dcouments to update
2. Specify *how* each document needs to be updated.

```
        db.restaurants.updateOne( 
           {_id: objectId},                       // document to be updated (by id)
           {$set: {name: "Salty's Seafood"}}      // $set used to rename the name to "Salty's Seafood"
        );
```

<br>

## How do you REPLACE a document?
In the same vein as the UPDATE method, when you REPLACE a document, you are replacing the ENTIRE document.  Be aware that when you do this, all of the properties in the object will be replaced with the new replaced document.
```
        db.restaurants.replaceOne(               // uses .replaceOne instead of .updateOne.
           {_id: objectId},
           {$set: {name: "Salty's Seafood"}}
        );
```






