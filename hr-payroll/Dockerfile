FROM maven:3.8.4-openjdk-11-slim AS api-gateway-service

RUN mkdir /api-gateway-build

WORKDIR /api-gateway-build

COPY . .

RUN mvn clean install



FROM openjdk:11

RUN mkdir /api-gateway-run

WORKDIR /api-gateway-run

COPY --from=api-gateway-service /api-gateway-build/target/hr-payroll-0.0.1-SNAPSHOT.jar .

CMD ["java", "-jar", "hr-payroll-0.0.1-SNAPSHOT.jar"]



# FROM openjdk:11
# VOLUME /tmp
# ADD ./target/hr-payroll-0.0.1-SNAPSHOT.jar hr-payroll.jar
# ENTRYPOINT ["java", "-jar", "/hr-payroll.jar"]