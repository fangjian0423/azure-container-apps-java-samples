FROM mcr.microsoft.com/openjdk/jdk:21-mariner AS build
WORKDIR /app
RUN tdnf install -y tar
COPY ../spring-petclinic/mvnw* /app/
COPY ../spring-petclinic/.mvn /app/.mvn
COPY ../spring-petclinic/pom.xml /app
COPY ../spring-petclinic/src /app/src
RUN ls -la /app
RUN chmod +x ./mvnw
RUN ./mvnw dependency:go-offline -B -Dproduction package


FROM mcr.microsoft.com/openjdk/jdk:21-mariner
ENV ARTIFACT_NAME=spring-petclinic-*.jar
COPY --from=build /app/target/${ARTIFACT_NAME} /usr/src/myapp/

EXPOSE 8080
CMD ["/usr/bin/java", "-jar", "/usr/src/myapp/${ARTIFACT_NAME}"]