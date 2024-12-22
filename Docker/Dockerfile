FROM maven:latest
RUN apt update
RUN apt install git -y
WORKDIR /app
RUN git clone https://github.com/shephertz/App42PaaS-Java-MySQL-Sample.git
RUN rm /app/App42PaaS-Java-MySQL-Sample/WebContent/Config.properties
ADD Config.properties app/App42PaaS-Java-MySQL-Sample/WebContent/Config.properties
RUN cd /app/App42PaaS-Java-MySQL-Sample && mvn clean && mvn install
