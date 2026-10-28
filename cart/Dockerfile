#************** multi stage builds ****************
# [Multi-stage build lo oke Dockerfile lo multiple FROM untayi. Build tools anni mundu stage lo (builder) untayi, final image lo run ki kavalsina files matrame copy avthayi. Result: image size chala taggutundi.]

# Stage 1: build
# Stage 1: dependencies install
FROM node:20-alpine3.23 AS builder

WORKDIR /opt/server

COPY package.json .
COPY *.js .

RUN npm install

# Stage 2: Run image
# Stage 2: final image
# so above ni docker file ga use chesukoni, inko docker file
FROM node:20-alpine3.23
#Below inka, nenu optimaisations chestanu ana mata, like RUN , SYSTEM USER, 
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop

ENV REDIS_HOST="redis" \
    CATALOGUE_HOST="catalogue" \
    CATALOGUE_PORT="8080"


WORKDIR /opt/server
USER roboshop
# here from builder /opt/server lo ne, man app code related files vunnai, so daani, matram copy chestunnam by root user only coping
#COPY enduku downlo pettanu ante, it will chanhe as per developers chioce the app code, anduke down load petta, it should not impact the othe Instructions(Layers), down lo vundi kabbati, deeni kinda vunnavi matrame imapact avthai, so just, application start chesta anthe deeni kinda simple..😁
COPY --from=builder /opt/server /opt/server 
#running container is or app code is by system user roboshop
CMD ["node", "server.js"]

# ****************** end of multi statge builds *************





# # image of nodejs :20 version i have taken from docker hub
# FROM node:20

# # “In traditional Linux deployments, we may keep application files under /app and manage the service using systemd. In Docker, we define the application's working directory using WORKDIR. The path is a design choice, and we follow the organization's standard directory structure.”
# # To download the extra content. mana istam vachina chota pettukovachu.[opt anedi konchem proper ga vuntundi]
# WORKDIR /opt/server

# #copying application code into home directory [. [dot]-> current directory]
# # COPY *.json . [copying all json files into current directory]
# COPY package.json .
# COPY *.js .

# #installing dependencies
# RUN npm install

# # Service file, environment anedi setup chestunna docker lo
# ENV REDIS_HOST="redis" \
#     CATALOGUE_HOST="catalogue" \
#     CATALOGUE_PORT="8080"
    
     
    


# #ExecStart=/bin/node /app/server.js
# #nenu present /opt/serverver lone vunna, so direct ga istunna.
# CMD ["node", "server.js"]