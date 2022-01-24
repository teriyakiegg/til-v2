# fargate

## Task CPU and memory
```
Amazon ECS task definitions for AWS Fargate require that you specify CPU and memory at the task level. Although you can also specify CPU and memory at the container level for Fargate tasks, this is optional. Most use cases are satisfied by only specifying these resources at the task level. The table below shows the valid combinations of task-level CPU and memory.
```
https://docs.aws.amazon.com/AmazonECS/latest/developerguide/AWS_Fargate.html