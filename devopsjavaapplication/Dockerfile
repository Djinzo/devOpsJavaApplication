FROM openjdk:17-oracle
ADD . /tmp
WORKDIR /tmp
USER root
RUN mv build/libs/devopsjavaapplication-0.0.1-SNAPSHOT.jar /app.jar && rm -rf /tmp
EXPOSE 8081
ENTRYPOINT ["sh", "-c", "java $JAVA_OPTS -jar /app.jar"]
