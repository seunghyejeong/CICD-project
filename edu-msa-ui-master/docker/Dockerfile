FROM tomcat:9-jre8-alpine
WORKDIR /usr/local/tomcat
COPY ../server.xml ./conf
RUN rm -rf ./webapps/*
ARG WAR_FILE=*.war
COPY ${WAR_FILE} ./edu-msa-ui-1.0.0.war
