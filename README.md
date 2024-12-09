# Falcon_Pymongo
Falcon webservice with Pymongo

<p align="center" width="100%">
    <img width="35%" src="https://github.com/jkaewprateep/Falcon_Pymongo/blob/main/mongoDB.jpg">
    <img width="9%" src="https://github.com/jkaewprateep/Falcon_Pymongo/blob/main/python.jpg">
    <img width="15%" src="https://github.com/jkaewprateep/Falcon_Pymongo/blob/main/kid_42.png"> </br> 
    <b> Python webservice with PyMongo </b> </br>
    <b> ( Picture from Internet ) </b> </br>
</p>

🧸💬 Invest time in implementation database no-SQL, documentary, migrational, and scalability. Cursor query support with an aggregation function creates useful database results from the selection, time, and post-query process. </br>
🐐💬 NO-SQL database is fast and you do not need to take time reading from database schemas when somebody tries to ```encrypt a field between tables, encryption algorithm, user access level, the name columns table separation, and more``` They are good at transaction log and will create the number of volumes if you are directly read from them ( they implement aggregation functions and one reason are you own aggregation functions without document and expertise in the specific database you read from aggregation name where modification may be limited by relational database -> you cannot see full statement inside the aggregate function when complied ) 👻💬💬 Boo ~! ~! </br>
🦭💬 MongoDB, MariaDB, and RedisDB are good for online transactions because we write more than read with contrast different ratios where we use aggregate results for delay processes, implementing ```pymongo``` is one good example of transaction logging and objects like transparent in program variable ( there are more complex query I wrote but they do not create benefits if we are talking about why MongoDB is good for online database ) </br>

🐑💬 ➰ Database and database schemas are intellectual property and project merchandise when MongoDB there are loosely schemas to  control database fields and their behavior their migration tasks are covered as merchandise as a relational database because it requires experience and works to prepare the same but in the non-SQL database where they do not have specific schemas than loosey schema transferable and migration is a plan and submitting as the database schema. There are many tools to perform this task such as MySQL migration and database conversion tools. </br>
🦁💬 Data drivers are not project merchandise by default but it required because they will need to be ready to perform when required they can support periods, links, and websites from the evaluation method can support this evidence when years of planning for data compatibility, and upgrade plan since the project start. </br>
🐯💬 Culture INFO, a custom needs to be submitted with version control and source code where they are tested and confirmed by the product and BU team ( my previous work to request ES or support for ES, it was an engineer patch it worked for a specific version you can have many ES but need to test and improved by the support team and BU ) - my complied works that is because I submitted as windows installer because Microsoft do magics inside the installer that make not often it fail. </br>

```
import array
from pymongo import MongoClient;
from pymongo import ReturnDocument;

from dateutil import parser
from bson import ObjectId

# 
from datetime import datetime

#
from bson.json_util import dumps
import json

class MongoDBDatabase :
    def __init__(self):
        super().__init__();
        return
    
    def get_database( self ):
        # 🧸💬 As an object read the database and return requirements connection with connection for database operations
        # Provide the mongodb atlas url to connect python to mongodb using pymongo
        # CONNECTION_STRING = "mongodb://localhost:27017/tg_subaccount";
        CONNECTION_STRING = "mongodb://localhost:27017";
        
        # Create a connection using MongoClient. You can import MongoClient or use pymongo.MongoClient
        client = MongoClient(CONNECTION_STRING)
        
        # Create the database for our example (we will use the same database throughout the tutorial
        return client['tg_subaccount']

    def insert_insertrecordlogging( self, header, url, response, ip_address, agent_id, requester ):
        # 🧸💬 Simple implement of transaction logging
        timestamp = datetime.utcnow();
        type = "INSERT RECORD";
        responsetime = datetime.utcnow();

        self.insert_requesttoDB( timestamp, type, header, url, response, ip_address, agent_id, responsetime, requester );

        return;

    def insert_insertorderlogging( self, header, url, response, ip_address, agent_id, requester ):
        # 🧸💬 Simple implement of transaction logging
        timestamp = datetime.utcnow();
        type = "INSERT ORDER";
        responsetime = datetime.utcnow();

        self.insert_requesttoDB( timestamp, type, header, url, response, ip_address, agent_id, responsetime, requester );

        return;
   
    def insert_requesttoDB( self, timestamp, type, header, url, response, ip_address, agent_id, responsetime, requester ):
        # 🧸💬 Simple implement of transaction logging
        item_1 = {
            "timestamp": timestamp,
            "type": type,
            "header": header,
            "url": url,
            "response": response,
            "ip_address": ip_address,
            "agent_id": agent_id,
            "responsetime": responsetime,
            "requester": requester
        }
        
        dbname = self.get_database()
        collection_name = dbname["requests"];
        collection_name.insert_one(item_1);
        
        return;

    def find_userrecordfromDB( self, username, requester ):
        # 🧸💬 Simple implement of transaction logging query
        item_1 = {
            "username" : username,
        };

        dbname = self.get_database()
        collection_name = dbname["robots"];
        resultset = collection_name.find_one(item_1);

        return resultset;

    def query_userstatusfromDB( self, username ):
        # 🧸💬 Simple implement of transaction logging query
        item_1 = {
            "username" : username,
        };

        dbname = self.get_database()
        collection_name = dbname["userstatus"];
        resultset = collection_name.find_one(item_1);

        userstatus = resultset["userstatus"];

        return userstatus;
```

---

<p align="center" width="100%">
    <img width="30%" src="https://github.com/jkaewprateep/advanced_mysql_topics_notes/blob/main/custom_dataset.png">
    <img width="30%" src="https://github.com/jkaewprateep/advanced_mysql_topics_notes/blob/main/custom_dataset_2.png"> </br>
    <b> 🥺💬 รับจ้างเขียน functions </b> </br>
</p
