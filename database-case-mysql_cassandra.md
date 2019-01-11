# database-case-mysql_cassandra

Reference: https://www.youtube.com/watch?v=psQzyFfsUGU  28 :00 - 32:00 

## MySQL 

- Reason: ACID - https://dev.mysql.com/doc/refman/5.6/en/mysql-acid.html

- Data: billing information, trasaction information, user information

- Solution: use at least two MySQL, one for main, the other as replica
    
    - Write: write data to main MySQL, and the other replicas will automatically sync. But only main mysql status will be acknowledge to the user.

    - Read: cach of most recent users.

    - Hot swap: once main is down, hot swap all the traffic to the replica.



## Cassandra

- Reason: can handle heavy read and heavy write.

- Data: all other large information

- Solution: Cassandra handle a heavy read and write. As the data grow bigger. We could maintain two kind of data: Live Viewing History and Compressed Viewing History.
  
    - Live Viewing History: is the data being the most recently use. We support high speed read/write of those data.
    - Compressed Viewing History: once some data are less likely being used recently. We could separate those data into another Cassandra node and compressed it to store.

