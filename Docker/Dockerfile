FROM maven:3.8.6-openjdk-11 AS build
RUN apt update
RUN apt install git -y
WORKDIR /app
RUN git clone https://github.com/shephertz/App42PaaS-Java-MySQL-Sample.git
RUN cd /app/App42PaaS-Java-MySQL-Sample && mvn clean && mvn install
FROM tomcat:jre8-alpine
COPY --from=build /app//App42PaaS-Java-MySQL-Sample/target/App42PaaS-Java-MySQL-Sample-0.0.1-SNAPSHOT.war /usr/local/tomcat/webapps
COPY Config.properties /usr/local/tomcat/ROOT
