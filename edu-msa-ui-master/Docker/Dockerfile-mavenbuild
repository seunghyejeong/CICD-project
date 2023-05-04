FROM maven:3.6.0-jdk-8-slim as builder
WORKDIR /home/ubuntu/workspace/practice-gitops/gitops-repository/edu-msa-ui-master
COPY pom.xml .
RUN mvn dependency:go-offline
COPY src ./src
RUN mvn clean package -DskipTests && \
    mkdir -p target && \
    cp target/edu-msa-ui-1.0.0.war target/ROOT.war

FROM openjdk:8-jre-slim
RUN apt-get update && apt-get install -y maven
WORKDIR /usr/local/tomcat/webapps/
COPY --from=builder /home/ubuntu/workspace/practice-gitops/gitops-repository/edu-msa-ui-master/target/ROOT.war .
EXPOSE 8080
CMD ["catalina.sh", "run"]
