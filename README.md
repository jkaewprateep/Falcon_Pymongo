# Falcon_Pymongo
Falcon webservice with Pymongo


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
