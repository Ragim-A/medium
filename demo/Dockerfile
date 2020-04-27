FROM openjdk:12-jdk-alpine AS builder
WORKDIR /code/
COPY build.gradle settings.gradle gradlew /code/
COPY gradle /code/gradle
RUN ./gradlew build || return 0
COPY . .
RUN ./gradlew build


FROM openjdk:12-jdk-alpine
WORKDIR /code/
COPY --from=builder /code/build/libs/demo.jar .
ENTRYPOINT ["java","-jar","demo.jar"]