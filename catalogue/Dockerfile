# image of nodejs :20 version i have taken from docker hub
FROM node:20

# To download the extra content. mana istam vachina chota pettukovachu.[opt anedi konchem proper ga vuntundi]
WORKDIR /opt/server

#copying application code into home directory [. [dot]-> current directory]
# COPY *.json . [copying all json files into current directory]
COPY package.json .
COPY *.json .

#installing dependencies
RUN npm install

# Service file, environment anedi setup chestunna docker lo
ENV MONGO="true" \
    MONGO_URL="mongodb://<MONGODB-SERVER-IPADDRESS>:27017/catalogue"