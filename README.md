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
🐐💬 NO-SQL database is fast and you do not need to take time reading from database schemas when somebody tries to encrypt a field between tables, encryption algorithm, user access level, the name columns table separation, and more they are good at transaction log and will create the number of volumes if you are directly read from them ( they implement aggregation functions and one reason are you own aggregation functions without document and expertise in the specific database you read from aggregation name where modification may be limited by relational database -> you cannot see full statement inside the aggregate function when complied ) 👻💬💬 Boo ~! ~! </br>
🦭💬 MongoDB, MariaDB, and RedisDB are good for online transactions because we write more than read with contrast different ratios where we use aggregate results for delay processes, implementing ```pymongo``` is one good example of transaction logging and objects like transparent in program variable ( there are more complex query I wrote but they do not create benefits if we are talking about why MongoDB is good for online database ) </br>

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

        # Provide the mongodb atlas url to connect python to mongodb using pymongo
        # CONNECTION_STRING = "mongodb://localhost:27017/tg_subaccount";
        CONNECTION_STRING = "mongodb://localhost:27017";
        
        # Create a connection using MongoClient. You can import MongoClient or use pymongo.MongoClient
        client = MongoClient(CONNECTION_STRING)
        
        # Create the database for our example (we will use the same database throughout the tutorial
        return client['tg_subaccount']

    def insert_insertrecordlogging( self, header, url, response, ip_address, agent_id, requester ):
        timestamp = datetime.utcnow();
        type = "INSERT RECORD";
        responsetime = datetime.utcnow();

        self.insert_requesttoDB( timestamp, type, header, url, response, ip_address, agent_id, responsetime, requester );

        return;

    def insert_insertorderlogging( self, header, url, response, ip_address, agent_id, requester ):
        timestamp = datetime.utcnow();
        type = "INSERT ORDER";
        responsetime = datetime.utcnow();

        self.insert_requesttoDB( timestamp, type, header, url, response, ip_address, agent_id, responsetime, requester );

        return;
   
    def insert_requesttoDB( self, timestamp, type, header, url, response, ip_address, agent_id, responsetime, requester ):
    
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

        item_1 = {
            "username" : username,
        };

        dbname = self.get_database()
        collection_name = dbname["robots"];
        resultset = collection_name.find_one(item_1);

        return resultset;

    def query_userstatusfromDB( self, username ):

        item_1 = {
            "username" : username,
        };

        dbname = self.get_database()
        collection_name = dbname["userstatus"];
        resultset = collection_name.find_one(item_1);

        userstatus = resultset["userstatus"];

        return userstatus;
```
