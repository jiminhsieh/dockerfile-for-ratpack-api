FROM debian

# Change to TW Repository
RUN rm /etc/apt/sources.list

RUN echo "deb http://opensource.nchc.org.tw/debian/ jessie main contrib non-free" | tee -a /etc/apt/sources.list
RUN echo "deb-src http://opensource.nchc.org.tw/debian/ jessie main contrib non-free " | tee -a /etc/apt/sources.list
RUN echo "deb http://security.debian.org/ jessie/updates main contrib non-free" | tee -a /etc/apt/sources.list
RUN echo "deb-src http://security.debian.org/ jessie/updates main contrib non-free" | tee -a /etc/apt/sources.list
RUN echo "deb http://opensource.nchc.org.tw/debian/ jessie-updates main contrib non-free" | tee -a /etc/apt/sources.list
RUN echo "deb-src http://opensource.nchc.org.tw/debian/ jessie-updates main contrib non-free" | tee -a /etc/apt/sources.list

RUN echo "" | tee -a /etc/apt/sources.list
RUN echo "# Oracle JDK 8" | tee -a /etc/apt/sources.list
RUN echo "deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main" | tee -a /etc/apt/sources.list
RUN echo "deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main" | tee -a /etc/apt/sources.list

RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys EEA14886
# Auto accept Oracle License
RUN echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections

RUN apt-get update && apt-get upgrade
RUN apt-get install -y --no-install-recommends apt-utils
RUN apt-get install -y --no-install-recommends oracle-java8-installer python git 
RUN apt-get install -y --no-install-recommends groovy gradle python-pip

RUN easy_install -U Distribute
RUN pip install logilab-common==0.63.0 
RUN pip install --upgrade setuptools

RUN cd ~/ && mkdir Repository
RUN cd ~/Repository && git clone https://JiminHsieh@bitbucket.org/JiminHsieh/robotframework-httplibrary.git && git clone https://JiminHsieh@bitbucket.org/JiminHsieh/robotframework-test-plan.git

RUN cd ~/Repository && git clone https://JiminHsieh@bitbucket.org/JiminHsieh/groovy-ratpack-api.git

RUN cd ~/Repository/robotframework-httplibrary && python bootstrap.py
RUN cd ~/Repository/robotframework-httplibrary && ./bin/buildout
RUN cd ~/Repository/groovy-ratpack-api && ./gradlew build

RUN mkdir ~/TestCases

WORKDIR /root/Repository/groovy-ratpack-api
CMD git pull && ./gradlew run

#EXPOSE 9090:9090
