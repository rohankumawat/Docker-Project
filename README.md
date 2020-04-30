## Docker
Docker is an open-source tool designed to make it easier, deploy, and run applications by using containers. It is a tool that is designed to benefit both developers and system administrators. 
## Docker Compose
Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a Compose file to configure your application's services. 
It is great for development, testing, and staging environments.
Using compose is simply a three steps process:
  1. Define your app's environment with a Dockerfile so it can be reproduced anywhere.
  2. Define the services that make up your app in docker-compose.yml so they can be run together in an isolated environment.
  3. Lastly, run docker-compose up and Compose will start and run your entire app.
In this project:
  1. Build the image.
  2. Run MySQL. 
  3. Run the image.
I've picked up a content management system 
docker-compose.yml file will setup Wordpress and MySQL with a single command.
## Requirements 
Make sure that you have the latest version of Docker and Docker Compose installed on your machine. 
If it isn't installed and you don't know how to install it, click [here](https://docs.docker.com/).

## Wordpress and MySQL
WordPress is a free and open-source content management system written in PHP and paired with a MySQL or MariaDB database. 
To run WordPress locally, you don't need Apache, MySQL server, XAMPP, Wamp and Mamp. All you need is Docker
### Creating the project
#### 1. Create an empty project directory.
```Bash
mkdir project
```
#### 2. Change into your project directory.
```Bash
cd project/
```
#### 3. Create a docker-compose.yml file that will start your WordPress blog and a separate MySQL instance with a volume mount for data persistence:
```Bash
vim docker-compose.yml
```
Or
```Bash
vi docker-compose.yml
```
Or
```Bash 
gedit docker-compose.yml
``` 
Use whichever text-editor you're comfortable with!
Then paste the content which is inside docker-compose.yml file I've attached here.
### 4. Save and close the file.
### 5. Build your project / Starting Containers 
```Bash
docker-compose up
```
Go to your web browser and run ```http://localhost:8080```. 
### 6. Removing Containers
To stop and remove all the containers use the ```down``` command
```Bash
docker-compose down
```
Use ```-v``` if you also want to rmeove the database volume which is used to persist the database:
```Bash
docker-compose down -v
```

## Understanding docker-compose.yml 
* ```dbos``` - It's just a name here. One can use any other name also. Here we run the MySQL image from the Docker Hub in version 5.7 with the password ```qwerty``` and other important information required to launch a MySQL container. To understand more, click [here](https://hub.docker.com/_/mysql).
* ```wordpressos``` - It's also a name here given for WordPress image. Here we build a Docker image for MySQL and map port 8080 on the host to port 80 inside the container. Then we give MySQL password, user, and database name via environment variable. Remember that you give the same password, username, and database name otherwise it'll give you and error.
* ```Why columes??``` - Since data in the containers is not persistent, i.e. if you stop the container and run it again, there will no longer be any data inside it, so to avoid this we add volume. Here add volume means that we make a separate volume for a particular container.
* ```volumes``` - Don't give spaces between ```wp_storage_new:``` and ```/var/www/html/``` as it would lead to an error.
