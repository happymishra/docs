# Start mongo services
sudo service mongod start

# Stop mongo service
sudo service mongod stop

# Mongo shell command
mongo

show dbs
show collections
use db


Creating multipe instance of mongodb on the same server
sudo mongod --dbpath /var/lib/mongodb2 --port 27020

sudo mongo --port 27020

# MongoDB connect with remote host
mongo -u user1 -p user1password <your_server_ip>/sampledb

# Give access to a database to a user
db.grantRolesToUser(
   "uat_compute",
   [ "readWrite" , { role: "read", db: "sliconsensusrevision" } ],
   { w: "majority" , wtimeout: 4000 }
)

# Replicas set for testing and development
https://docs.mongodb.com/manual/tutorial/deploy-replica-set-for-testing/

sudo service mongod start --replSet rs0

mongod --replSet rs0 --port 27018 --bind_ip localhost --dbpath /srv/mongodb/rs0-1 --smallfiles --oplogSize 128

mongod --replSet rs0 --port 27019 --bind_ip localhost --dbpath /srv/mongodb/rs0-2 --smallfiles --oplogSize 128

# start mondo on the required port
sudo mongo --port 27019

# get indexes
db.colname.getIndexes()

# get monogodb engine information
db.serverStatus().storageEngine

# get version
db.version()



Config1 - 226
Replicata connfig - 227

228 and 229 - Data replicat set - Shard 1

230 and 231 - Shard 2


















sh.status('verbose')

db.collection.getShardDistribution()

sh.shardCollection('consensuscomputeinfo.sliconsensusrevision_one', {'companyid': 1, 'revisiondpid': 1})

db.collection.explain('exectutionStats')

sh.isBalancerRunning()

var status = db.serverStatus()
status.connections

convertShardKeyToHashed( ObjectId("5b2be413c06d924ab26ff9ca") )

db.chunks.find({'ns': 'consensuscomputeinfo.slicon_comp_hash'}).pretty()

db.chunks.find({"shard" : "shard0000"},{"shard":1,"jumbo":1}).pretty()

sh.status('consensuscomputeinfo.sliconsensusrevision')

db.runCommand({getLog: 'global'})

db.runCommand( { "connPoolStats" : 1 } )

Number of Chunks	Migration Threshold
Fewer than 20	                 2
20-79	                         4
80 and greater	               8

https://docs.mongodb.com/manual/reference/method/db.collection.latencyStats/



db.createCollection('slicon_range')
db.slicon_range.createIndex({'cid': 1, 'rid': 1})
sh.shardCollection('consensuscomputeinfo.slicon_range', {'cid': 1, 'rid': 1})

sh.enableSharding('insights_bigd')


db.createCollection('slirevision')
db.slirevision.createIndex({'cid': 1, 'rid': 1},  { unique: true } )
sh.shardCollection('insights_bigd.slirevision', {'cid': 'hashed'})

db.createCollection('sliconsensusrevision')
db.sliconsensusrevision.createIndex({'cid': 1, 'rid': 1},  { unique: true } )
sh.shardCollection('insights_bigd.sliconsensusrevision', {'cid': 'hashed'})

db.createCollection('slivaactualsrevision')
db.slivaactualsrevision.createIndex({'cid': 1, 'rid': 1},  { unique: true } )
sh.shardCollection('insights_bigd.slivaactualsrevision', {'cid': 'hashed'})

db.createCollection('normalizedrevision')
db.normalizedrevision.createIndex({'cid': 1, 'rid': 1},  { unique: true } )
sh.shardCollection('insights_bigd.normalizedrevision', {'cid': 'hashed'})

db.createCollection('consensusrevision')
db.consensusrevision.createIndex({'cid': 1, 'rid': 1},  { unique: true } )
sh.shardCollection('insights_bigd.consensusrevision', {'cid': 'hashed'})

db.createCollection('vaactualsrevision')
db.vaactualsrevision.createIndex({'cid': 1, 'rid': 1},  { unique: true } )
sh.shardCollection('insights_bigd.vaactualsrevision', {'cid': 'hashed'})

db.createCollection('schedulerevision')
db.schedulerevision.createIndex({'cid': 1, 'rid': 1},  { unique: true } )
sh.shardCollection('insights_bigd.schedulerevision', {'cid': 'hashed'})

db.createCollection('scheduleconsensusrevision')
db.scheduleconsensusrevision.createIndex({'cid': 1, 'rid': 1},  { unique: true } )
sh.shardCollection('insights_bigd.scheduleconsensusrevision', {'cid': 'hashed'})

db.createCollection('schvaactualsrevision')
db.schvaactualsrevision.createIndex({'cid': 1, 'rid': 1},  { unique: true } )
sh.shardCollection('insights_bigd.schvaactualsrevision', {'cid': 'hashed'})

db.sliconsensusrevision.remove({})
db.slirevision.remove({})
db.slivaactualsrevision.remove({})
db.normalizedrevision.remove({})
db.consensusrevision.remove({})
db.vaactualsrevision.remove({})

db.sliconsensusrevision.drop()
db.slirevision.drop()
db.slivaactualsrevision.drop()
db.normalizedrevision.drop()
db.consensusrevision.drop()
db.vaactualsrevision.drop()
db.schedulerevision.drop()
db.scheduleconsensusrevision.drop()
db.schvaactualsrevision.drop()


# Group by
db.sliconsensusrevision.aggregate([
  {"$group": {_id: "$rid", count: {$sum:1}}}
])

db.createCollection('slirevision')
db.slirevision.createIndex({'cid': 1, 'rid': 1}, { unique: true })

db.createCollection('sliconsensusrevision')
db.sliconsensusrevision.createIndex({'cid': 1, 'rid': 1}, { unique: true } )

db.createCollection('slivaactualsrevision')
db.slivaactualsrevision.createIndex({'cid': 1, 'rid': 1}, { unique: true } )

db.createCollection('normalizedrevision')
db.normalizedrevision.createIndex({'cid': 1, 'rid': 1}, { unique: true } )

db.createCollection('consensusrevision')
db.consensusrevision.createIndex({'cid': 1, 'rid': 1}, { unique: true } )

db.createCollection('vaactualsrevision')
db.vaactualsrevision.createIndex({'cid': 1, 'rid': 1}, { unique: true } )

db.createCollection('schedulerevision')
db.schedulerevision.createIndex({'cid': 1, 'rid': 1}, { unique: true } )

db.createCollection('scheduleconsensusrevision')
db.scheduleconsensusrevision.createIndex({'cid': 1, 'rid': 1}, { unique: true } )

db.createCollection('schvaactualsrevision')
db.schvaactualsrevision.createIndex({'cid': 1, 'rid': 1}, { unique: true } )

db.getUser('username')

db.slirevision.createIndex({'ct': 1})




db.slirevision.find({'cid':18941}).count()
db.sliconsensusrevision.find({'cid':18941}).count()
db.slivaactualsrevision.find({'cid':18941}).count()
db.normalizedrevision.find({'cid':18941}).count()
db.consensusrevision.find({'cid':18941}).count()
db.vaactualsrevision.find({'cid':18941}).count()
db.schedulerevision.find({'cid':18941}).count()
db.scheduleconsensusrevision.find({'cid':18941}).count()
db.schvaactualsrevision.find({'cid':18941}).count()

db.slirevision.remove({'cid':13059})
db.slirevision.remove({'cid':13059})
db.slivaactualsrevision.remove({'cid':13059})
db.normalizedrevision.remove({'cid':13059})
db.consensusrevision.remove({'cid':13059})
db.vaactualsrevision.remove({'cid':13059})
db.schedulerevision.remove({'cid':13059})
db.scheduleconsensusrevision.remove({'cid':13059})
db.schvaactualsrevision.remove({'cid':13059})


db.slirevision.update({}, {$set: {'ct': new Date()}}, false, true)
db.sliconsensusrevision.update({}, {$set: {'ct': new Date()}}, false, true)
db.slivaactualsrevision.update({}, {$set: {'ct': new Date()}}, false, true)
db.normalizedrevision.update({}, {$set: {'ct': new Date()}}, false, true)
db.consensusrevision.update({}, {$set: {'ct': new Date()}}, false, true)
db.vaactualsrevision.update({}, {$set: {'ct': new Date()}}, false, true)
db.schedulerevision.update({}, {$set: {'ct': new Date()}}, false, true)
db.scheduleconsensusrevision.update({}, {$set: {'ct': new Date()}}, false, true)
db.schvaactualsrevision.update({}, {$set: {'ct': new Date()}}, false, true)



db.slirevision.update({'cid': 13059}, {$set: {'ct': new Date()}}, false, true)
db.sliconsensusrevision.update({'cid': 13059}, {$set: {'ct': new Date()}}, false, true)
db.slivaactualsrevision.update({'cid': 13059}, {$set: {'ct': new Date()}}, false, true)
db.normalizedrevision.update({'cid': 13059}, {$set: {'ct': new Date()}}, false, true)
db.consensusrevision.update({'cid': 13059}, {$set: {'ct': new Date()}}, false, true)
db.vaactualsrevision.update({'cid': 13059}, {$set: {'ct': new Date()}}, false, true)
db.schedulerevision.update({'cid': 13059}, {$set: {'ct': new Date()}}, false, true)
db.scheduleconsensusrevision.update({'cid': 13059}, {$set: {'ct': new Date()}}, false, true)
db.schvaactualsrevision.update({'cid': 13059}, {$set: {'ct': new Date()}}, false, true)

db.slirevision.update({}, {$set: {'ct': new Date()}}, false, true)
db.sliconsensusrevision.update({}, {$set: {'ct': new Date()}}, false, true)
db.slivaactualsrevision.update({}, {$set: {'ct': new Date()}}, false, true)
db.normalizedrevision.update({}, {$set: {'ct': new Date()}}, false, true)
db.consensusrevision.update({}, {$set: {'ct': new Date()}}, false, true)
db.vaactualsrevision.update({}, {$set: {'ct': new Date()}}, false, true)
db.schedulerevision.update({}, {$set: {'ct': new Date()}}, false, true)
db.scheduleconsensusrevision.update({}, {$set: {'ct': new Date()}}, false, true)
db.schvaactualsrevision.update({}, {$set: {'ct': new Date()}}, false, true)

db.slirevision.remove({})
db.sliconsensusrevision.remove({})
db.slivaactualsrevision.remove({})
db.normalizedrevision.remove({})
db.consensusrevision.remove({})
db.vaactualsrevision.remove({})
db.schedulerevision.remove({})
db.scheduleconsensusrevision.remove({})
db.schvaactualsrevision.remove({})

db.sliconsensusrevision.remove({'cid': {$in:[13807, 20493]}})
db.slirevision.remove({'cid': {$in:[13807, 20493]}})
db.slivaactualsrevision.remove({'cid': {$in:[13807, 20493]}})
db.normalizedrevision.remove({'cid': {$in:[13807, 20493]}})
db.consensusrevision.remove({'cid': {$in:[13807, 20493]}})
db.vaactualsrevision.remove({'cid': {$in:[13807, 20493]}})
db.schedulerevision.remove({'cid': {$in:[13807, 20493]}})
db.scheduleconsensusrevision.remove({'cid': {$in:[13807, 20493]}})
db.schvaactualsrevision.remove({'cid': {$in:[13807, 20493]}})

db.sliconsensusrevision.find({'cid': {$in:[13807, 20493]}}).count()
db.slirevision.find({'cid': {$in:[13807, 20493]}}).count()
db.slivaactualsrevision.find({'cid': {$in:[13807, 20493]}}).count()
db.normalizedrevision.find({'cid': {$in:[13807, 20493]}}).count()
db.consensusrevision.find({'cid': {$in:[13807, 20493]}}).count()
db.vaactualsrevision.find({'cid': {$in:[13807, 20493]}}).count()
db.schedulerevision.find({'cid': {$in:[13807, 20493]}}).count()
db.scheduleconsensusrevision.find({'cid': {$in:[13807, 20493]}}).count()
db.schvaactualsrevision.find({'cid': {$in:[13807, 20493]}}).count()

https://stackify.com/mongodb-performance-tuning/

https://www.datadoghq.com/blog/monitoring-mongodb-performance-metrics-mmap/

https://medium.com/@igorkhomenko/troubleshooting-mongodb-100-cpu-load-and-slow-queries-da622c6e1339

https://stackoverflow.com/questions/34951683/mongodb-constantly-high-cpu-usage
