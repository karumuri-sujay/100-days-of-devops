### Task:

The Nautilus DevOps team is
conducting application deployment tests on selected application servers.
 They require a nginx container deployment on `Application Server 3`. Complete the task with the following instructions:

1. On `Application Server 3` create a container named `nginx_3` using the `nginx` image with the `alpine` tag. Ensure container is in a `running` state.

#### Solution:

Run the below commands

```
docker create --name nginx_3 --image nginx_3
output- <id>
docker start <id> 
```
