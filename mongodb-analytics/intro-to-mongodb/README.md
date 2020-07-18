# Mongodb intro course

https://account.mongodb.com/account/login

connect via shell(`C:\mongodb_shell\bin`)

```
mongo "mongodb+srv://cluster0.wzlug.mongodb.net/coursera1" --username admin
```

### Getting first data into Mongodb

I already loaded a bunch of sample data, so need to make sure I am careful about how I name stuff, etc.

created a db/namespace (?) called `coursera1` and a collection called `movies_initial`.

***Note: looks like the Atlas web interface has changed since the course was created***
***As of 2020-07-18***

Where I found documentation on `mongoimport`:
 - https://docs.atlas.mongodb.com/command-line-tools/#connect-with-mongoimport

```
mongoimport --host atlas-hndvh0-shard-0/cluster0-shard-00-00.wzlug.mongodb.net:27017,cluster0-shard-00-01.wzlug.mongodb.net:27017,cluster0-shard-00-02.wzlug.mongodb.net:27017 --ssl --username admin --password r7hgth4PonRH5TQG --authenticationDatabase admin --db coursera1 --collection movies_initial --type CSV --file movies_initial.csv
```

note though, have to add the `--headerline` parameter to the command above.


