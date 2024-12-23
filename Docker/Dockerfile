FROM maven:latest AS build
RUN apt update
RUN apt install git -y
WORKDIR /app
RUN git clone https://github.com/shephertz/App42PaaS-Java-MySQL-Sample.git
RUN rm /app/App42PaaS-Java-MySQL-Sample/WebContent/Config.properties
COPY Config.properties app/App42PaaS-Java-MySQL-Sample/WebContent/Config.properties
RUN cd /app/App42PaaS-Java-MySQL-Sample && mvn clean && mvn install
FROM tomcat:jre8-alpine
COPY --from=build /app/App42PaaS-Java-MySQL-Sample/target/App42PaaS-Java-MySQL-Sample.war /usr/local/tomcat/webapps
COPY --from=build app/App42PaaS-Java-MySQL-Sample/WebContent/Config.properties /usr/local/tomcat/ROOT