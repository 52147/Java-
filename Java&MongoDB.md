# Use Java to operate MongoDB
MongoDB allows import the json file and csv file.

## Step
1. import the json file or csv file in mongodb
2. do some quert
3. see the output


## 0. Convert the xml file to json file

## 1. Import the json file
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
## 2. Query the data

## 3. Get the output

## Challenge part
I try to import the json file in mongoDB through Java, not working.
Got this error: 
Exception in thread "main" org.bson.json.JsonParseException: JSON reader was expecting a name but found '<eof>'.
