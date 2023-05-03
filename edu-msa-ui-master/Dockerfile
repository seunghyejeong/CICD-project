FROM maven:3.6.0-jdk-8-slim
WORKDIR /home/ubuntu/workspace/practice-gitops/gitops-repository/edu-msa-ui-master
COPY pom.xml .
RUN mvn dependency:go-offline
COPY src ./src
RUN mvn package
EXPOSE 8080
CMD ["java", "-jar", "./target/edu-msa-ui-1.0.0.war"]
