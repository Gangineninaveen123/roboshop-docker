# image of nodejs :20 version i have taken from docker hub
#alpine vachesi, base image os, chala takiuva mb tisukundi so anduke use chestunnam.
FROM node:20-alpine3.23 

# Create a group and user for system user
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop

# To download the extra content. mana istam vachina chota pettukovachu.[opt anedi konchem proper ga vuntundi]
WORKDIR /opt/server
#above working directory[/opt/server] ki ee system user[roboshop], ni ownership istunam, [-R -> istam directories vunte]
RUN chown -R roboshop:roboshop /opt/server

# the below vunna, instructions anni after USER-> roboshop user thone run avtundi anamata.
USER roboshop

#copying application code into home directory [. [dot]-> current directory]
# COPY *.json . [copying all json files into current directory]
COPY package.json .
COPY *.js .

#installing dependencies
RUN npm install

# Service file, environment anedi setup chestunna docker lo
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"


#ExecStart=/bin/node /app/server.js
#nenu present /opt/serverver lone vunna, so direct ga istunna.
CMD ["node", "server.js"]