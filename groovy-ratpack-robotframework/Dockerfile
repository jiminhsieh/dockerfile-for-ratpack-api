FROM debian

RUN echo "" | tee -a /etc/apt/sources.list
RUN echo "# OpenJDK 8" | tee -a /etc/apt/sources.list
RUN echo "deb http://cloudfront.debian.net/debian unstable main" | tee -a /etc/apt/sources.list
RUN echo "deb-src http://cloudfront.debian.net/debian unstable main" | tee -a /etc/apt/sources.list

RUN apt-get update 
RUN apt-get install -y openjdk-8-jdk groovy gradle python python-pip git 

RUN pip install robotframework

#RUN mkdir Repository
#RUN cd Repository
#RUN git clone

EXPOSE 9090
