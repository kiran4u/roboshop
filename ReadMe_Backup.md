
1. MogoDb should be running
2. Catalogue should be running
    Note: 
    Containers should have proper name to connect each other.
    By default you are not able to connect on the name, you cna connect using IP address.
    Everytime we create a container the IP Address may change.


3. Connect MongoDb and Catalogue
4. Connect web to Catalogue


Networks:
Bridge -> By default
host
overlay
macvlan

Default Bridge Network can not resolve on names.
Docker recommends to create our own bridge network.

Command: 
ip a
docker network create roboshop
Advanatges:
Using this approach Containers are isolated from another project. AND
We can  communicate using names between containers.

Commands:
 213  docker network create roboshop
  214  docker network ls
  215  ip a
  216  clear
  217  docker run -d --name mongodb mongodb:v1
  218  docker ps
  219  docker inspect mongodb
  220  docker network ls
  221  docker network connect roboshop mongodb
  222  docker network ls
  223  docker inspect mongodb
  224  docker network ls
  225  docker run -d --name catalogue catalogue:v1
  226  docker run -d --name catalogue --network roboshop catalogue:v1
  227  docker ps
  228  docker rm -f 103dc6657ab8
  229  docker run -d --name catalogue --network roboshop catalogue:v1
  230  docker ps
  231  docker inspect catalogue
  232  docker logs catalogue


  # Shell Script:
  for i in web mongo catalogue user cart mysql shipping; do cd $i ; docker build -t $i:v1 . ; cd ..; done






