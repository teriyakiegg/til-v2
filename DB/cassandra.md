# cassandra
## Cassandra Basics
https://cassandra.apache.org/_/cassandra-basics.html

```
When data is inserted into the cluster, the first step is to apply a hash function to the partition key. The output is used to determine what node (based on the token range) will get the data.
```