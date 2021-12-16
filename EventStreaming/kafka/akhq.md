# akhq
- Cluster can be viewed in a list and selected.
- Nodes can be viewed in a list and view their Configs and Logs.
- Topics can be viewed in a list.
  - You can see the last time a record was procured.
  - You can see the Consumer Groups associated with a Topic and see the current Lag.
- Details of a Topic can be viewed.
  - If you have permission, you can produce a record from the Topic Details screen.
  - You can also see the schema associated with the record.
  - If you have permission, you can delete all records from the Topic Details screen.
- You can also see the Schema Registry for each Topic.
  - You can also see the version history

## Topic config

### retention.ms
- The value of retention.ms is going to determine when the Topic records that can be viewed from akhq will disappear.
  - https://docs.confluent.io/platform/current/installation/configuration/topic-configs.html

## Consumer group config

### offset
https://dattell.com/data-architecture-blog/understanding-kafka-consumer-offset/