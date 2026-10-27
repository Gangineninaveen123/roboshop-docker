# image of nodejs :20 version i have taken from docker hub
FROM node:20

# “In traditional Linux deployments, we may keep application files under /app and manage the service using systemd. In Docker, we define the application's working directory using WORKDIR. The path is a design choice, and we follow the organization's standard directory structure.”
# To download the extra content. mana istam vachina chota pettukovachu.[opt anedi konchem proper ga vuntundi]
WORKDIR /opt/server


# Service file, environment anedi setup chestunna docker lo
# ILA KUDA RAYACHU, OR oke ENV  petti, last lo foraward slash ina ivvachu.
ENV MONGO="true"
ENV REDIS_URL="redis://redis:6379"
ENV MONGO_URL="mongodb://mongodb:27017/users" 


#******** layesrs, will not impact, beacause app code may chage freqently *************
#copying application code into home directory [. [dot]-> current directory]
# COPY *.json . [copying all json files into current directory]
COPY package.json .
COPY *.js .

#installing dependencies
RUN npm install
# the below command, just to check, disk size when increase in RUN Instaructions, lets see
RUN apt-get update \
    && apt-get install -y net-tools git \
    && apt-get clean
    

#ExecStart=/bin/node /app/server.js
#nenu present /opt/serverver lone vunna, so direct ga istunna.
CMD ["node", "server.js"]