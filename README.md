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
|      To find your current location                |   ```db```                                                        |
|      To show current databases                    |   ```show dbs```                                            |
|      To use (and/or create) a database            |   ```use <database-name>```                                        |
|                                                   |                                                                |
|                                                   |                                                                |
|                                                   |                                                                |
|      To show collections in database              |   ```show collections```                                      |
|      To show all collections in database by name  |   ```db.getCollectionNames()```                              |
|      To create a new collection                   |   ```db.createCollection('name-of-collection');```          |
|                                                   |                                                                |
|                                                   |                                                                |
|                                                   |                                                                |
|      To delete database                           |   ```db.dropDatabase();```                                         |
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








```JavaScript
        {
           "_id":{"$oid":"59074c7c057aaffaafb0da64"},
           "address":{"building":"2911",
           "coord":[-73.982241,40.576366],
           "street":"West   15 Street",
           "zipcode":"11224"},
           "borough":"Brooklyn",
           "cuisine":"Italian",
           "grades":[{"date":{"$date":"2014-12-18T00:00:00.000Z"},
           "grade":"A","score":13},
           {"date":{"$date":"2014-05-15T00:00:00.000Z"},
           "grade":"A","score":12},
           {"date":{"$date":"2013-06-12T00:00:00.000Z"},
           "grade":"A","score":9},
           {"date":{"$date":"2012-02-06T00:00:00.000Z"},
           "grade":"A","score":9}],
           "name":"Gargiulo's Restaurant",
           "restaurant_id":"40365784"}
```



