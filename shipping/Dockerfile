# maven through image from docker hub
FROM maven

#Working directory /opt/server, in the place of /app, no issues, as per company, working directory ll be mentioned.
WORKDIR /opt/server

#copying application code into home directory [. [dot]-> current directory]
# COPY src .[copying all java files into current directory]
COPY pom.xml .
COPY src .

#installing packages and dependencies, mvn clean package
RUN mvn clean package

# Target nunchi bayataku tisukostha .jar file ni, so
RUN mv /opt/server/target/shipping-1.0.jar /opt/server/shipping.jar

# Service file, environment anedi setup chestunna docker lo
ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="mysql"


#ExecStart=/bin/java -jar /app/shipping.jar
#nenu present /opt/serverver lone vunna, so direct ga istunna.
CMD ["java","-jar","shipping.jar"]