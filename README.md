
# NoSQL Databases - Intro


In this section, you'll learn about querying a popular NoSQL database -- MongoDB. 


## Objectives

You will be able to:  
 
* Describe why NoSQL is useful


## Why NoSQL?

Relational databases are a cornerstone of a modern technology. They're reliable, dependable, and they seem to be pretty much everywhere. Since their invention at IBM by Edgar Codd in 1970, they've rapidly grown to be used all over the place. Their creation allowed companies to track, store, and analyze data in ways that simply couldn't be done before. For the majroity of situations, they're a great choice. However, as technology has progressed into the era of internet and smartphones, we've run into many different sorts of data that aren't a natural fit for a relational format. Let's examine a few of these situations, and see why NoSQL might be a better choice. 

Let's assume that we need to store chat logs between customer service and customers through a web interface. These chats could be very short, or very long -- some chats may only be 2 or 3 messages, while others may conceivably be in the hundreds or thousands. For each message in the chat, we want to store metadata associated with the message, so that we can know things like which party sent the message, the time it was sent, the time the other party read the message, etc. This is a great use case for a NoSQL database, because it would be a very poor fit for a relational database. For starters, each chat can be any size, meaning that we can't just clearly define a table that links which messages belong to which chat. If every chat had only five messages, we might be able to make it work, with a column for "message 1", "message 2", and so on -- but we can't, because a chat has no set size, and can always grow larger in the future. A relational database would also waste a lot of space storing redundant information, and getting all the messages in a chat could result in some nasty runtimes for our SQL query if this data was stored in separate tables in something like the third normal format. 

There are a several kinds of NoSQL databases, including: 

- Document Stores 
- Key-Value Stores and Column Stores 
- Graph Databases 
- RDDs and Big Data 

In this section, we will explore **MongoDB**, a popular **Document Store** database.  

## Document Stores

A **_Document Store_** is a database that stores records as unique documents in the database. These documents can be arbitrarily long, and can even contain other documents inside of them! The chat log example we saw above is a prime use case for a document store. In a document store, we could store each message and its accompanying metadata as a document, and then embed each of those documents in order in a chat document. In this way, we can easily access the data as needed. 

In these Document Stores, each document contains key-value pairs, with the actual data being stored in as the value. This makes Document Stores incredibly flexible, because each document can be unique. There is no constraint saying each document must have the same keys! This makes it great for working with data where we don't know what shape it will take (as we saw above, with chat logs that can be arbitrarily long or short), or perhaps when we don't know what data will be stored at all. This would be a problem in a relational database, because we would need to know what column the data belongs in before we could store it. With a Document Store, we can just create a key on the fly for the data that matters to us!

Note that while this flexibility makes it easy for us to store data on the fly, this also makes it harder for us to query data and get exactly what we need. Since each different document can potentially have its own **_Schema_**, this means that we have to know what we are looking for. This also means that we have to be diligent in our naming conventions, because `chatLog` is different than `ChatLog`. This means that if we run a query across all documents to get all data with the key `chatLog`, we'll completely miss any data where they key is written as `ChatLog`!

##### Popular  Document Store Databases: MongoDB and Couchbase

| <img src="images/mongo-db-logo.png" height=60% width=60%> | <img src="images/couchbase-logo.png"> |
|---------------------|---------------------|



## MongoDB

In this section you will install MongoDB on your machine, and then add some data to it, so that we can learn to store data and write queries using MongoDB. By the end of this section, you'll be able to do all the same things in MongoDB as you can in SQLite3!

## Summary

In this lesson, we learned about NoSQL databases and their importance along with a brief intro of **Document Stores**, a popular cateogry of NoSQL databases. 
