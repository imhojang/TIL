## MongoDB basics 

---

Date: 20190903

commands:

- `mongod` turn on database server
- `mongo` turn on mongo shell (database server must be running in order to work)

---

`mongod`

- by default 

  - stores data in /data/db
  - listens for connections from clients on port 27017
  - [MongoDB Docs](https://docs.mongodb.com/manual/tutorial/manage-mongodb-processes/#start-mongod-processes)

- can specify data directory with `mongo --dbpath <directory>` command

  