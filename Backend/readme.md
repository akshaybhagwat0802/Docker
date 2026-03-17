 ## 1) Open terminal and apply following commands 
 ```bash
sudo -i &&
sudo apt update
```
## 2) install the docker into terminal 
```bash
sudo apt install docker.io -y
```
## 3) start and enabel teh docker 
```bash
sudo systemctl start docker &&
sudo systemctl enable docker
```
## 4) add the docker into the usergroup 
```bash
sudo adduser -aG docker ubuntu
```
## 5) create a group 
```bash
newgrp docker
```
## 6) change the permissions of the user
```bash
chmod 777 var/run/docker.sock
```
## 7) clone the repository 
```bash
git clone <repo link>
```
## 8) change the repo to the backend 
```bash
cd backend/
```
## 9)copy application.properties file 
```bash
cp src/main/resources/application.properties .
```
## 10) add the rds endpoint and dbname and password into application.properties file 
```bash
vim application.properties
```
## 11) create a dockerfile
```bash
 FROM maven:3.8.3-openjdk-17
COPY . /opt/
WORKDIR /opt/
RUN rm -rf src/main/resources/application.properties
RUN cp -r application.properties src/main/resources/
RUN mvn clean package
WORKDIR target/
EXPOSE 8080
CMD ["java","-jar","student-registration-backend-0.0.1-SNAPSHOT.jar"]
```
## 12) create a docker image for backend
```bash
docker build -t backend .
```
## 13) create a docker container for backend 
```bash
docker run -d -p 8080:8080 backend .
