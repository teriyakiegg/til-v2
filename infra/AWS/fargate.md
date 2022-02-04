# fargate

## Task CPU and memory
```
Amazon ECS task definitions for AWS Fargate require that you specify CPU and memory at the task level. Although you can also specify CPU and memory at the container level for Fargate tasks, this is optional. Most use cases are satisfied by only specifying these resources at the task level. The table below shows the valid combinations of task-level CPU and memory.
```
https://docs.aws.amazon.com/AmazonECS/latest/developerguide/AWS_Fargate.html


## Supported Configurations
```
CPU Memory Values
0.25 vCPU	0.5 GB, 1 GB, and 2 GB
0.5 vCPU	Min. 1 GB and Max. 4 GB, in 1 GB increments
1 vCPU	Min. 2 GB and Max. 8 GB, in 1 GB increments
2 vCPU	Min. 4 GB and Max. 16 GB, in 1 GB increments
4 vCPU	Min. 8 GB and Max. 30 GB, in 1 GB increments
```
https://aws.amazon.com/fargate/pricing/