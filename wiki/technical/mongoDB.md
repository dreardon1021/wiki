# Basics

MongoDB is a document database designed for the ease of development and scaling. Documents or a record, are data structures that are composed of field, value points. These are are BSON objects which are simply JSON Objects. These objects usually have a specific field/key called "_id".

# Relevant Terminology

MongoDB uses the CRUD methodology which stands for, Create, Read, Update, Delete.

Collections - Analogous to tables in relational databases. An example would be a collection of users

Document Validation - V3.2+, Allows validation to make sure schema is accurate

Indexes - Special data structures that store a small portion of the collections data set in a easy to traverse form. Helps limit the amount of time it takes to inspect the documents int he database. MongoDB creates a unique index on the _id field during the creation of a collection

Transaction - A unit of work performed within a databse management system against a databse. Reperesent any change in a database

# Terminal commands

Open mongo shell on terminal CLI - mongo

Display current database - db

Switch to a database with specified name - db insertDBNameHere

Create a new db and collection:

```
  use myNewDB

  db.myNewCollection1.insertOne(  objectToStoreHere )

```

note: If a database does not exist, mongoDB creates the database when you first store data for that database. insertOne() will create a new collection in the db, if this was used in a new empty database, it will create and establish the new database


listCollections/db.getCollectionsInfo() - list collections

create a single key descending index on the 'name' field:

View index names: db.collection.getIndexes()


# CRUD related commands

###### Create

db.users.insertOne(        <-- collection
  {
    name: 'sue',        <--field:value
    age: 26             <--field:value
  }
)

###### Read

db.users.find(                <-- collection
  {
    {age: {$gt: 18} }         <--query criteria, age is greater than 18
    {name: 1, address: 1}     <--projection
  }
).limit(5)                    <--cursor modifier

###### Update

db.users.updateMany(
  {
    {age: {$lt: 18} }             <--Update Filter, age is less than 18
    {$set: {status: reject} }     <--projection
  }
)

###### Delete

db.deleteMany(
  { status: "reject }  <-- delete filter
)