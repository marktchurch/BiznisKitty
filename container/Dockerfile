FROM ubuntu:14.04

RUN sudo apt-get -y install software-properties-common wget
RUN sudo add-apt-repository ppa:openjdk-r/ppa
RUN sudo apt-get update
RUN sudo apt-get -y install openjdk-8-jdk
RUN wget -O /tmp/apache-tomcat-8.0.23.tar.gz "http://apache.claz.org/tomcat/tomcat-8/v8.0.23/bin/apache-tomcat-8.0.23.tar.gz"
WORKDIR /opt
RUN sudo tar xvfz /tmp/apache-tomcat-8.0.23.tar.gz
RUN sudo ln -s apache-tomcat-8.0.23 apache-tomcat
RUN sudo useradd -m tomcat
RUN sudo chown -R tomcat:tomcat apache-tomcat*
RUN sudo rm /tmp/apache-tomcat-8.0.23.tar.gz
RUN sudo wget --no-check-certificate -O /opt/apache-tomcat/webapps/unikitty.war "https://ec2-54-175-42-12.compute-1.amazonaws.com/nexus/service/local/repositories/snapshots/content/io/unikitty/unikitty/1.0-SNAPSHOT/unikitty-1.0-20150620.045006-3.war"
EXPOSE 8080
ENTRYPOINT sudo -u tomcat /opt/apache-tomcat/bin/catalina.sh run

