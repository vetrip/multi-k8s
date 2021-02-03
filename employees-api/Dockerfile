# stage-0 extract layered jars
FROM adoptopenjdk:11-jre-openj9 as builder

ARG JAR_FILE=target/*.jar

COPY ${JAR_FILE} application.jar
# extract layered images
RUN java -Djarmode=layertools -jar application.jar extract

# stage-1
# copy layered dependencies
FROM adoptopenjdk:11-jre-openj9

COPY --from=builder dependencies ./

COPY --from=builder snapshot-dependencies ./

COPY --from=builder spring-boot-loader ./

COPY --from=builder application ./

ENTRYPOINT [ "java","org.springframework.boot.loader.JarLauncher"]
