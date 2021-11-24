# dockerlearn
## Get Start
- create a new file call Dockerfile
- we need a base image to run the app
- in this example using latest debian image
- or using node.js image
```docker:
 FROM node:latest
 
 RUN mkdir -p /app/src
 
 WORKDIR  /app/src 
 
 COPY package.json . or /app/src
 
 RUN npm install
 
 COPY . .  # is the current directory to destination current directory
 
 EXPOSE 3000 # in order to see app in browser
 
 CMD ["npm", "start"]
```
- this will build docker image
- using docker command to build docker image
```command
docker build . -t  nameofimageapp # build image
#  find image
docker images
3 run image
docker run 

```
- in VS CODE extension run it on click
## run multiple service with multiple container
- using .yml extension for configue docker file
- name this example as docker-compose.yml
``` yaml
version: "3.9"
    
services:
  db:
    image: mysql:5.7
    volumes:
      - db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: somewordpress
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress
    
  wordpress:
    depends_on:
      - db
    image: wordpress:latest
    volumes:
      - ./wp-content:/var/www/html/wp-content
    ports:
      - "8000:80"
    restart: always
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
      WORDPRESS_DB_NAME: wordpress
volumes:
  db_data: {}
  wordpress_data: {}
```
- run the compose file
```ubuntu
# run as a background task up 
docker-compose up -d 
# pull the task backdown
docker-compose down
```
## deploy to docker hub
- docker tag IMAGEID username/projectname:tagname
- docker push username/projectname:tagname
