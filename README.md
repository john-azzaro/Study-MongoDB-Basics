# MongoDB Basics Study

<br>

## What is MongoDB Basics Study?
The "MongoDB Basics Study" explores the basic functionality of the MongoDB including installation, basic concepts, etc.

<br>


## How do you install MongoDB?
Installing MongoDB is a little tricky in that you need to do a few things like editing path variables, using command prompt,
and adding a default storage file for your Mongo databases on your local machine.  Follow the steps below to get started with
MongoDB and take special note of some of the observations and issues you might encounter and how to resolve them.


**Step 1: Download MongoDB from https://www.mongodb.com/download-center/community :**
> *note: make sure you download the community*


**Step 2: Once the download is complete, install on your local machine:**
> *note: DO NOT INSTALL MONGODB COMPASS at this time.  A few issues made it difficult to install... install compass AFTER installation.* 


**Step 3: Navigate to the installation folder, find "mongod" and copy the directory**
> *note: Your installation file directory might be different, but it should look like this: C:\Program Files\MongoDB\Server\4.0\bin*
> *factual note: "mongod" is "mongo daemon" which is the mongoDB server*


**Step 4: In your search bar, look for "advanced system settings", select "enviroment variables", edit the PATH variable by adding the previous path.**
> *note: make sure you put the entire path (i.e. "C:\Program Files\MongoDB\Server\4.0\bin" ) in so that it works correctly*

**Step 5: Install MongoDB Compass to use the database GUI (graphical user interface).**
> *note: make sure you install the community verison*

**Step 6: In command prompt, run "mongod" for the first time and (if needed) create a "db" directory for your future data**
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
When you use the interactive mongo shell, you are essentially interfacing with your database.

**Step 1: First, run "mongod" in command prompt** 
> *note: once you run "mongod", you wont need to use the command prompt window much because we will be using Gitbash to interface with the database, so you can set it aside*
```
mongod                            
```


**Step 2: Second, run "mongo" in Gitbash to start using the interactive mongo shell**
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
