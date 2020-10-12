# Running the ddocker-compose

### Fix access to Lavarel log
```
docker-compose exec learning-locer bash 
chmod 777 /var/www/html/app/storage/logs/laravel-2020-10-09.log
```

### Fix indexes ([see more](https://github.com/LearningLocker/learninglocker/issues/854#issuecomment-240531357))

Log into mongo
```
mongo mongo
use learninglocker
``` 

Fix indexes

```
db.statements.createIndex({stored: 1})
db.statements.createIndex({timestamp: 1})
db.statements.createIndex({active: 1})
db.statements.createIndex({voided:1})
db.statements.createIndex({lrs_id:1})
db.statements.createIndex({lrs_id:1, active:-1, voided:1})
db.statements.createIndex({lrs_id:1, 'statement.actor.mbox':1} )
db.statements.createIndex({'statement.actor.mbox':1})
db.statements.createIndex({lrs_id:1, 'statement.actor.account.name':1, 'statement.actor.account.homePage':1})
db.statements.createIndex({lrs_id:1, 'statement.actor.mbox':1} )
db.statements.createIndex({lrs_id:1, 'statement.verb.id':1})
db.statements.createIndex({lrs_id:1, 'statement.object.id':1})
db.statements.createIndex({lrs_id: 1, stored:-1})
db.statements.createIndex({lrs_id: 1, timestamp:-1})
db.statements.createIndex({'statement.id':1, lrs_id:1})
```

### Add learning locker to hosts

```
[ip address]    [alias]
127.0.0.1       learning-locker
```