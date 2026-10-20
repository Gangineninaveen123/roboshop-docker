# image of nodejs :20 version i have taken from docker hub
FROM node:20

# “In traditional Linux deployments, we may keep application files under /app and manage the service using systemd. In Docker, we define the application's working directory using WORKDIR. The path is a design choice, and we follow the organization's standard directory structure.”
# To download the extra content. mana istam vachina chota pettukovachu.[opt anedi konchem proper ga vuntundi]
WORKDIR /opt/server

#copying application code into home directory [. [dot]-> current directory]
# COPY *.json . [copying all json files into current directory]
COPY package.json .
COPY *.js .

#installing dependencies
RUN npm install

# Service file, environment anedi setup chestunna docker lo
ENV MONGO="true" \
    REDIS_URL="redis://redis:6379" \
    MONGO_URL="mongodb://mongodb:27017/users" 
    


#ExecStart=/bin/node /app/server.js
#nenu present /opt/serverver lone vunna, so direct ga istunna.
CMD ["node", "server.js"]