#IndexedDB

![f](https://imgur.com/shFLteo.png)


## IDBrequest Object

Every time we initiate a transaction it returns an `IDBrequest` object. Just like with a promise, or XHR we must handle this object with `onsuccess` or `onerror`. Remember indexedDB is asynchronous.
 
https://github.com/bluehabit/Ajax/blob/master/Projects/LearningIndexedDB/Put/readme.md
get the posts from LMD as well

Important note, sometimes for changes like updating or deleting a record in a database to take place, you must either go into the application tab and refresh the database, or close the console and reopen it again. 

![f](https://imgur.com/K5netce.png)

`.put`, `.add` and many other methods for the objectstore return an `IDBrequest` object with the property `result` which contains the `primaryKey` of your query. MDN documentation on this is a bit poor unfortunately. 

![f](https://imgur.com/4vZhlPt.png)

## Schema

When the `onupgradeneeded` event triggers, and we create our object store we must define a `schema`. A `schema` is just a way to define how we will be storing data within our database.

```
openRequest.onupgradeneeded = function(event) {
  var db = event.target.result;
  console.log(db)
  var objectStore = db.createObjectStore("centralPark", {
    autoIncrement: true
  });

  for (var prop in friendsData) {
    objectStore.add(friendsData[prop]);
  }
};
```

## KeyPaths 

Key Paths are what we will use to *access* the data within our database. 

We have three different approaches for Key Paths with indexedDB. A Key Path is synonymous with a primary key. It is just a property that is specific to a record. Whether that is a unique ID or email address. 

### 1. Key Path + Auto Increment 

 Allows you to set your own key path /primary key called `myKey` and then auto increment it. Since you provided a key path it is stored on the object `inline` as a key:value pair. 

![f](https://imgur.com/Q4lbhDA.png)


### 2. Key Path Only

Useful when your records themselves already have a primary key that you want to use. For example an email address, or their own unique ID that already exists as a property.

![f](https://imgur.com/YGLXGTh.png)

### 3. Auto Increment Only

When you use auto increment only, it is NOT stored inline on the record itself as a key value pair.

![f](https://imgur.com/8NUjlsS.png)
