FROM ubuntu AS build
RUN apt-get update
RUN apt-get install -y openjdk-8-jdk
RUN apt-get install -y maven
RUN mkdir /words
WORKDIR /words
COPY pom.xml .
COPY src src
RUN mvn verify

FROM ubuntu AS run
RUN apt-get update
RUN apt-get install -y openjdk-8-jre
RUN mkdir /words
WORKDIR /words
COPY --from=build /words/target/words.jar .
COPY --from=build /words/target/dependency dependency
EXPOSE 8080
CMD java -Xmx8m -Xms8m -jar words.jar
