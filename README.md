# Installation
```sh
git clone https://JiminHsieh@bitbucket.org/JiminHsieh/dockerfile.git
cd groovy-ratpack-robotframework/
docker build -t ratpack-api .
docker -i -t -p $port:9090 ratpack-api 
```
