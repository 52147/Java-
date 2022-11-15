# Use Java to operate MongoDB
MongoDB allows import the json file and csv file.

## Step
1. import the json file or csv file in mongodb
2. do some quert
3. see the output


## 0. Convert the xml file to json file

## 1. Import the json file
```java
import java.io.BufferedReader;
import java.io.FileReader;

import org.bson.Document;
import com.mongodb.MongoClient;
import com.mongodb.client.MongoCollection;
import com.mongodb.client.MongoDatabase;

public class InsertJsonFileToMongoDB {
	@SuppressWarnings("resource")
	public static void main(String[] args) {
		
		try {
			// 1. connect to database at local host 27017
			MongoClient mk = new MongoClient("localhost", 27017);
			// 2. get the database name
			MongoDatabase md = mk.getDatabase("db1");
			// 3. create a collection in db1
			MongoCollection<Document> collection = md.getCollection("test5");
			// 4. read the json file
			BufferedReader br = new BufferedReader(new FileReader("temp.json"));
			String docs = null;
			// 5. insert the json data in db1
			while ((docs = br.readLine()) != null) {
				collection.insertOne(Document.parse(docs));
				// print the document that insert in db1
				System.out.println(docs);
			}
			System.out.println("Documents inserted successfully");
			// 6. close the mongo client
			mk.close();
		} catch (Exception e) {
			System.out.println(e.getMessage());
		}
	}
}
```

### Output
### `Java console`
```
11�� 13, 2022 12:35:24 �U�� com.mongodb.diagnostics.logging.JULLogger log
INFO: Cluster created with settings {hosts=[localhost:27017], mode=SINGLE, requiredClusterType=UNKNOWN, serverSelectionTimeout='30000 ms', maxWaitQueueSize=500}
11�� 13, 2022 12:35:24 �U�� com.mongodb.diagnostics.logging.JULLogger log
INFO: Opened connection [connectionId{localValue:1, serverValue:150}] to localhost:27017
11�� 13, 2022 12:35:24 �U�� com.mongodb.diagnostics.logging.JULLogger log
INFO: Monitor thread successfully connected to server with description ServerDescription{address=localhost:27017, type=STANDALONE, state=CONNECTED, ok=true, version=ServerVersion{versionList=[5, 0, 9]}, minWireVersion=0, maxWireVersion=13, maxDocumentSize=16777216, roundTripTimeNanos=950000}
11�� 13, 2022 12:35:24 �U�� com.mongodb.diagnostics.logging.JULLogger log
INFO: Opened connection [connectionId{localValue:2, serverValue:151}] to localhost:27017
{"_id":{"$oid":"5e6e879a9cd239bf672f78a0"},"profile":{"game_id":8495,"fed_id":"3ed824a2-d497-5ef0-aa39-9238853c022c","created":{"$date":"2012-03-14T08:49:58.649Z"},"modified":{"$date":"2000-04-19T13:51:46.134Z"},"total_spent":{"$numberDecimal":"334.6"},"total_playtime":{"$numberDecimal":"323.2"},"size":8,"credential":"anonymous:45b59e5d31ed8e03c57483661ee738599e12ef0b","current_client_id":"89957:27872:1.8.0ag:android:etowoof.kp","_client_id":58618,"last_session":{"$date":"2007-01-08T15:37:48.661Z"},"last_purchase":{"$date":"2000-04-26T08:17:04.71Z"},"total_refund":{"$numberDecimal":"4775.5"},"total_transactions":532,"xp":96177733,"level":6,"locale":{"country":"us","language":"en"}},"player":{"Key":"103ccf0b6240f9b64a2a76ff6415847ba356e99bdeeaa04f1370f4d36423c502cf7899005c9527996bc9ead95fd37590ae1d11c94d789d8751f418b2e"}}
{"_id":{"$oid":"5e6e879a9cd239bf672f78a1"},"profile":{"game_id":5008,"fed_id":"c60ec11e-82ec-5278-be09-f7c5e4dd3ea6","created":{"$date":"2000-12-19T22:36:48.911Z"},"modified":{"$date":"2007-05-30T02:37:19.39Z"},"total_spent":{"$numberDecimal":"0"},"total_playtime":{"$numberDecimal":"4460.8"},"size":89,"credential":"anonymous:40d709ec77267b57382ad5d337d9e6b2721db0aa","current_client_id":"28039:27872:1.8.0ag:android:vudep.com","_client_id":46949,"last_session":{"$date":"2003-12-17T13:32:16.334Z"},"last_purchase":{"$date":"2009-05-15T06:45:28.927Z"},"total_refund":{"$numberDecimal":"7020.7"},"total_transactions":428,"xp":80081358,"level":33,"locale":{"country":"it","language":"it"}},"player":{"Key":"2f2088370c1af3a0ee29aa1f310978c95161cef1f5964c4ae20fd8ac15e3c9a6aee0bd3ebf3d81bdee64d69d63eadf4fef49e8a0572e87b1b45e73feb"}}
{"_id":{"$oid":"5e6e879a9cd239bf672f78a2"},"profile":{"game_id":2463,"fed_id":"9acf88be-5222-5eb4-aa29-f32b407139d4","created":{"$date":"2009-04-15T23:56:33.873Z"},"modified":{"$date":"2016-11-18T18:51:29.074Z"},"total_spent":{"$numberDecimal":"3495"},"total_playtime":{"$numberDecimal":"3775.4"},"size":271,"credential":"anonymous:a678c3636498fb337f85effd0d9eef3c19e8a651","current_client_id":"96348:27872:1.8.0ag:android:kitov.km","_client_id":25883,"last_session":{"$date":"2018-12-07T05:58:11.095Z"},"last_purchase":{"$date":"2004-12-24T21:23:25.891Z"},"total_refund":{"$numberDecimal":"5498.4"},"total_transactions":343,"xp":26461767,"level":52,"locale":{"country":"us","language":"en"}},"player":{"Key":"f45075d2e1b8a345aa846a2f55d7386c6132daf41a9ccc1033df38b323a735610a32e54a30fa7b96d5e12f831cc0ce0f046c62b8d3a15c9fbbcf463dc"}}
readStartDocument can only be called when CurrentBSONType is DOCUMENT, not when CurrentBSONType is END_OF_DOCUMENT.
```
### `Mongosh`
```
db1> db.test2.find()
[
  {
    _id: ObjectId("5e6e879a9cd239bf672f78a0"),
    profile: {
      game_id: 8495,
      fed_id: '3ed824a2-d497-5ef0-aa39-9238853c022c',
      created: ISODate("2012-03-14T08:49:58.649Z"),
      modified: ISODate("2000-04-19T13:51:46.134Z"),
      total_spent: Decimal128("334.6"),
      total_playtime: Decimal128("323.2"),
      size: 8,
      credential: 'anonymous:45b59e5d31ed8e03c57483661ee738599e12ef0b',
      current_client_id: '89957:27872:1.8.0ag:android:etowoof.kp',
      _client_id: 58618,
      last_session: ISODate("2007-01-08T15:37:48.661Z"),
      last_purchase: ISODate("2000-04-26T08:17:04.710Z"),
      total_refund: Decimal128("4775.5"),
      total_transactions: 532,
      xp: 96177733,
      level: 6,
      locale: { country: 'us', language: 'en' }
    },
    player: {
      Key: '103ccf0b6240f9b64a2a76ff6415847ba356e99bdeeaa04f1370f4d36423c502cf7899005c9527996bc9ead95fd37590ae1d11c94d789d8751f418b2e'
    }
  },
  {
    _id: ObjectId("5e6e879a9cd239bf672f78a1"),
    profile: {
      game_id: 5008,
      fed_id: 'c60ec11e-82ec-5278-be09-f7c5e4dd3ea6',
      created: ISODate("2000-12-19T22:36:48.911Z"),
      modified: ISODate("2007-05-30T02:37:19.390Z"),
      total_spent: Decimal128("0"),
      total_playtime: Decimal128("4460.8"),
      size: 89,
      credential: 'anonymous:40d709ec77267b57382ad5d337d9e6b2721db0aa',
      current_client_id: '28039:27872:1.8.0ag:android:vudep.com',
      _client_id: 46949,
      last_session: ISODate("2003-12-17T13:32:16.334Z"),
      last_purchase: ISODate("2009-05-15T06:45:28.927Z"),
      total_refund: Decimal128("7020.7"),
      total_transactions: 428,
      xp: 80081358,
      level: 33,
      locale: { country: 'it', language: 'it' }
    },
    player: {
      Key: '2f2088370c1af3a0ee29aa1f310978c95161cef1f5964c4ae20fd8ac15e3c9a6aee0bd3ebf3d81bdee64d69d63eadf4fef49e8a0572e87b1b45e73feb'
    }
  },
  {
    _id: ObjectId("5e6e879a9cd239bf672f78a2"),
    profile: {
      game_id: 2463,
      fed_id: '9acf88be-5222-5eb4-aa29-f32b407139d4',
      created: ISODate("2009-04-15T23:56:33.873Z"),
      modified: ISODate("2016-11-18T18:51:29.074Z"),
      total_spent: Decimal128("3495"),
      total_playtime: Decimal128("3775.4"),
      size: 271,
      credential: 'anonymous:a678c3636498fb337f85effd0d9eef3c19e8a651',
      current_client_id: '96348:27872:1.8.0ag:android:kitov.km',
      _client_id: 25883,
      last_session: ISODate("2018-12-07T05:58:11.095Z"),
      last_purchase: ISODate("2004-12-24T21:23:25.891Z"),
      total_refund: Decimal128("5498.4"),
      total_transactions: 343,
      xp: 26461767,
      level: 52,
      locale: { country: 'us', language: 'en' }
    },
    player: {
      Key: 'f45075d2e1b8a345aa846a2f55d7386c6132daf41a9ccc1033df38b323a735610a32e54a30fa7b96d5e12f831cc0ce0f046c62b8d3a15c9fbbcf463dc'
    }
  }
]
```
## 2. Query the data
- https://cmql.org/playmongo/
- https://stackoverflow.com/questions/70089317/how-to-do-a-word-count-in-mongodb

```
		/**
		 * Test the query
		 */
		MongoClient mk = new MongoClient("localhost", 27017);
		MongoDatabase md = mk.getDatabase("db1");
		MongoCollection<Document> collection = md.getCollection("test6");

		// Query: find the match text
		collection.createIndex(Indexes.text("title"));
		// 1. find the text "fast"
		Bson filter = Filters.text("fast");
		// 2. print the doc that contain "fast"
		collection.find(filter).forEach((Consumer<? super Document>) doc -> System.out.println(doc.toJson()));

		// Query: find # of doc that title is "Fast 5"
		// 1. use aggregate to group the value
		collection.aggregate(
				// 2. pass a list to perform aggregate stage
				Arrays.asList(
						// 3. find the "title" field is "Fast 5"
						Aggregates.match(Filters.text("Fast 5")),
//						Aggregates.match(Filters.eq("title", "Fast 5")),
						// 4. group the matching doc by "_id" field
						// accumulating doc for each distinct value "_id"
						Aggregates.group("$_id", Accumulators.sum("count", 1))))
				// 5. print the output
				.forEach((Consumer<? super Document>) doc -> System.out.println(doc.toJson()));
```




## 3. Get the output

## Challenge part
I try to import the json file in mongoDB through Java, not working.
Got this error: 
Exception in thread "main" org.bson.json.JsonParseException: JSON reader was expecting a name but found '<eof>'.
