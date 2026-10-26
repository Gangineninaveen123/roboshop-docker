#************** multi stage builds ****************
# [Multi-stage build lo oke Dockerfile lo multiple FROM untayi. Build tools anni mundu stage lo (builder) untayi, final image lo run ki kavalsina files matrame copy avthayi. Result: image size chala taggutundi.]

# Stage 1: dependencies install
FROM node:20-alpine3.23 AS builder

WORKDIR /opt/server

COPY package.json .
COPY *.js .

RUN npm install

# Stage 2: final image
# so above ni docker file ga use chesukoni, inko docker file
FROM node:20-alpine3.23
#Below inka, nenu optimaisations chestanu ana mata, like RUN , SYSTEM USER, 
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop

ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"

WORKDIR /opt/server
USER roboshop
# here from builder /opt/server lo ne, man app code related files vunnai, so daani, matram copy chestunnam.
COPY --from=builder /opt/server /opt/server
CMD ["node", "server.js"]

# ****************** end of multi statge builds *************

# # image of nodejs :20 version i have taken from docker hub
# #alpine vachesi, base image os, chala takiuva mb tisukundi so anduke use chestunnam.
# FROM node:20-alpine3.23 

# # Create a group and user for system user
# RUN addgroup -S roboshop && adduser -S roboshop -G roboshop

# # To download the extra content. mana istam vachina chota pettukovachu.[opt anedi konchem proper ga vuntundi]
# WORKDIR /opt/server




# #copying application code into home directory [. [dot]-> current directory]
# # COPY *.json . [copying all json files into current directory]
# COPY package.json .
# COPY *.js .

# #installing dependencies
# RUN npm install

# #above working directory[/opt/server] ki ee system user[roboshop], ni ownership istunam, [-R -> istam directories vunte]
# RUN chown -R roboshop:roboshop /opt/server
# # Service file, environment anedi setup chestunna docker lo
# ENV MONGO="true" \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"


# # the below vunna, instructions anni after USER-> roboshop user thone run avtundi anamata.
# USER roboshop
# # na flow below di
# #[root tho files copy chesi, dependencies install chesi, tarvata chown -R tho anni files roboshop ki ichesi, last lo USER roboshop[system user] tho switch chesaru. Container start ayinappudu node server.js roboshop tho run avthundi, root tho kaadu. Idi valid pattern, work avthundi.]
# #ExecStart=/bin/node /app/server.js
# #nenu present /opt/serverver lone vunna, so direct ga istunna.
# CMD ["node", "server.js"]