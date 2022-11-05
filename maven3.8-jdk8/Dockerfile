FROM maven:3.8.6-amazoncorretto-8 as builder
ARG PROJECT
WORKDIR /usr/local/src/web-app
COPY . .
COPY maven3.8-jdk8/settings.xml /root/.m2/settings.xml
RUN mvn -f demo/pom.xml clean package -Dmaven.test.skip=true
RUN mv /usr/local/src/web-app/$PROJECT/target/*.war /usr/local/src/web-app/$PROJECT/target/ROOT.war

FROM tomcat:9.0.68-jdk8-corretto
ARG PROJECT
WORKDIR /usr/local/tomcat
#COPY maven3.8-jdk8/config.properties /usr/local/tomcat/conf/config.properties
COPY --from=builder /usr/local/src/web-app/$PROJECT/target/ROOT.war /usr/local/tomcat/webapps

EXPOSE 8080
