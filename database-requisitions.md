## Database requisitions

When deciding on what type of data store to select for a software system, vendor project, program, event e.g a PVT database for an election, the following guide is the criteria by which ICT recommends.

### Definitions 

There are two types of datastores supported at NDI. SQL or relational databases and NoSQL or Non-relational database. Relational databases are structured, like phone books that store phone numbers and addresses. e.g. MSSQL or MySQL. 

Non-relational databases are document-oriented and distributed, like file folders that hold everything from a person’s address and phone number to their Facebook likes and online shopping preferences. e.g. Firebase Cloud Firestore, MongoDB.

### When a system warrants a relational database

* Hierarchical data. By its nature, hierarchical data is relational. That is "data that owns other data".

    * You could represent an entire hierarchy as documents in a Non-relational database, but the ongoing management of that will be considerably more difficult than in a relational database, and will be up to your application layer to maintain. That’s a lot of non-trivial code.

    * Permissions/permission groups/LDAP or ADFS type of systems permissions warrant a relational database.

    * The NDI organizational "rollup" structure, where employees roll up to managers who roll up to directors, etc warrants a relational database.

* Relationships between data. This is somewhat related to hierarchical data, but instead of ownership, you need peer relationships. Think of a social network as an example.

    * You could reference other documents’ _id’s to form relationships but as with hierarchical data, requires having a very complex application layer to enforce these relationships that are inherently baked into relational or graph databases.

### When a system warrants a non-relational database

* You are collecting pieces of information that may vary from user-to-user. For example, conditional responses in a form or survey.

* You may need to collect additional pieces of information in the future quickly.

* You need to persist a running log file to be queryable quickly.

Tradeoffs when using a non-relational or NoSQL database:

* No built-in ACID compliance [up until recently](https://www.mongodb.com/blog/post/multi-document-transactions-in-mongodb), e.g. a transaction that involves the modification of several document collections as one atomic unit

* No concept of relational integrity between collections, e.g. if you rely on a collection’s _id on another collection’s document and you outright delete the parent document, there’s no cascading updates to update/delete/mark the child as null

* If you’re familiar with any variant of SQL, the querying language will seem alien to you initially.

* If you’re familiar with JavaScript, the querying language will seem natural to you.

### ICT Supported Datastores

* MySQL

* PostgreSQL

* ElasticSearch

* MongoDB

* Firebase CloudFirestore

Resources: 

IBM [Field Guide to the World of Modern Data Stores](http://www-01.ibm.com/common/ssi/cgi-bin/ssialias?htmlfid=CDW12359USEN#) ([PDF](https://drive.google.com/open?id=14f9VC4sByHcdjancHUJFxTx3z8dco7zs))

