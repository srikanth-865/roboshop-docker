FROM maven:3.9.16  AS builder
WORKDIR /app
COPY src ./src
COPY pom.xml .
#this RUn command do as build maven java application compile and create jar file into /app/target/shipping-1.0.jar  clean removes the previous target/ build directory.
RUN mvn clean package   && \
#java created this /app/target/shipping-1.0.jar so it move and rename as shipping.jar
    mv target/shipping-1.0.jar shipping.jar 


# Java is portable not OS dependent, application built in windows can run in Linux we are using eclipse for RUNNing
FROM eclipse-temurin:17-jre-alpine
EXPOSE 8080
WORKDIR /app
RUN addgroup -S roboshop && adduser -S -G roboshop roboshop && \
    chown -R roboshop:roboshop /app
    #so we need only RUn time so we take jar only
COPY --from=builder /app/shipping.jar . 
USER roboshop
CMD ["java", "-jar" , "shipping.jar"]












##First time running code 
# FROM maven:3.9.16 
# WORKDIR /app
# COPY src ./src
# COPY pom.xml .
# RUN mvn clean package
# RUN mv target/shipping-1.0.jar shipping.jar 
# EXPOSE 8080
# CMD ["java", "-jar" , "shipping.jar"]