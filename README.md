# Before installation
> This dockerfile works on debian jessie & centos 7 with docker that I had been verified.
> But if you try to use **boot2docker**, please follow below instruction.

![VirtualBox](http://i.imgur.com/LzYL8L6.png)
> Please **uncheck** red box!!! Or VirtualBox will crash, when you try to build docker image.

# Installation of docker image
```sh
git clone https://JiminHsieh@bitbucket.org/JiminHsieh/dockerfile.git
cd groovy-ratpack-robotframework/
docker build -t $image_name .
docker -i -t -p $outer_port:9090 $image_name
```

# How to use this image first time
```sh
docker -i -t -p $outer_port:9090 $image_name
```

# After the first time
```sh
docker start $CONTAINER_ID
```
It will work for you.