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

  

mongodb+srv://<id>:<password>@vc-project-codewars-v4l7q.azure.mongodb.net/test?retryWrites=true&w=majority

mongoimport --uri "mongodb+srv://<id>:<password>@vc-project-codewars-v4l7q.azure.mongodb.net/test?ssl=true&replicaSet=myAtlasRS&authSource=admin" --collection problems --drop --file ~/Documents/sample_problems.json

mongoimport --host vc-project-codewars-shard-00-02-v4l7q.azure.mongodb.net:27017, --ssl -u <id> -p '<password>' --authenticationDatabase admin  --db test --collection problems --drop --file ~/Documents/sample_problems.json

mongodb+srv://imhojang:ck984875@vc-project-codewars-v4l7q.azure.mongodb.net/test?retryWrites=true&w=majority



**this**

mongoimport --host vc-project-codewars-shard-00-02-v4l7q.azure.mongodb.net:27017 --ssl -u <id> -p '<password>' --authenticationDatabase admin  --db test --collection problems --drop --jsonArray --file ~/Documents/sample_problems.json



**this**

mongo "mongodb+srv://vc-project-codewars-v4l7q.azure.mongodb.net/test" --username <id>