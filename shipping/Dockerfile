#*** from multi stage builds ****************
# [Multi-stage build lo oke Dockerfile lo multiple FROM untayi. Build tools anni mundu stage lo (builder) untayi, final image lo run ki kavalsina files matrame copy avthayi. Result: image size chala taggutundi.]


#for JRE taking official image in docker hub[JDK , we dont want, because (.jar file tisukoni stage:2, run lo use chestam)]
# Stage 1: build
# Stage 1: dependencies install
# maven (JDK -> Which do the compile the code and make it as build)
FROM maven AS builder
WORKDIR /opt/server
COPY pom.xml .
COPY src /opt/server/src
# i can keep, multiple run commands into single run command only.[ll see in image creation in 2nd Dockerfile, downside]
RUN mvn clean package
#&& mv /opt/server/target/shipping-1.0.jar /opt/server/shipping.jar

# stage:2 , run the image
# while running the image at run time, i don't need build, and i have copied, so at run time, i do't need maven, to build the image[from builder i am taking from build1-> image cretion], so jre official image i have taken.
FROM eclipse-temurin:17-jre-alpine
#WORKDIR / pwd
WORKDIR /opt/server
# EXPOSE , just for info
EXPOSE 8080
#system user
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
# service file of shipping
ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="mysql"

#copy from builder, stage1, .jar file and pom.xml files[buikld file and app code[.jar-> packaging done[ready for deployement]]]
COPY --from=builder /opt/server/target/shipping-*.jar /opt/server/shipping.jar
#user -> customised bride network-> name is roboshop[from boboshop to shipping container, so this shipping cantainer can communicate to other containers, in the one VM itself]
USER roboshop
# running conatainer.
CMD ["java","-jar","shipping.jar"]

#************* multi stage builds ***************





# # maven through image from docker hub
# FROM maven

# #Working directory /opt/server, in the place of /app, no issues, as per company, working directory ll be mentioned.
# WORKDIR /opt/server

# #copying application code into home directory [. [dot]-> current directory]
# # COPY src .[copying all java files into current directory]
# COPY pom.xml .
# COPY src /opt/server/src

# #installing packages and dependencies, mvn clean package
# RUN mvn clean package

# # Target nunchi bayataku tisukostha .jar file ni, so
# RUN mv /opt/server/target/shipping-1.0.jar /opt/server/shipping.jar

# # Service file, environment anedi setup chestunna docker lo
# ENV CART_ENDPOINT="cart:8080" \
#     DB_HOST="mysql"


# #ExecStart=/bin/java -jar /app/shipping.jar
# #nenu present /opt/serverver lone vunna, so direct ga istunna.
# CMD ["java","-jar","shipping.jar"]