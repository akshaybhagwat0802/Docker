## 1) change the directory to frontend 
```bash
cd frontend/
```
## 2) add the public ip of instacne in .env file 
```bash
vim .env
```
## 3) create docker file 
```bash
vim dockerfile
```
## 4) write docker file for frontend 
```bash
FROM node:25-alpine
COPY . /opt/
WORKDIR /opt
RUN npm install && npm run build
RUN apk update && apk add apache2
RUN cp -rf dist/* /var/www/localhost/htdocs/
EXPOSE 80
CMD ["httpd","-D","FOREGROUND"]
```
## 5) build an docker image
```bash
docker build -t frontend .
```
## 6) create a container for backend 
```bash
docker run -d -p 80:80 frontend .
```

