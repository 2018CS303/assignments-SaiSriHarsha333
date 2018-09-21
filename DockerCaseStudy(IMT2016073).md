# Docker Case Study

1. Create a list of users in a txt file.

 ```
user_1
user_2
user_3
user_4
```
2. Execute the following shell script to create docker container for each user in the above list.

 ```sh
echo -n "Enter users file:"
read file
while read user
    do
      docker create -it --name $user ubuntu /bin/bash
    done < $file
```
Here, I have created base ubuntu image. it can be replaced with any base linux image of your choice.

3. Allocated containers can be used by executing following shell script.
```sh
echo -n "Enter username:"
read user
docker start $user
docker attach $user
```
Any training environment can be installed from here.

4. Monitor the containers by using
```sh
echo -n "Enter username of the container to be monitored:"
read user
docker logs -f $user
```

5. Delete the containers

 ```sh
echo -n "Enter users file:"
read file
while read user
    do
      docker stop $user
      docker rm $user
    done < $file
```
