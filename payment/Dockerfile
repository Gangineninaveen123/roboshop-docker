#***** Multi stage builds ***************
#stage 1: Image building
FROM python:3.9 AS builder
WORKDIR /opt/server
COPY requirements.txt .
COPY *.py .
COPY payment.ini .
RUN pip3 install -r requirements.txt

#Run image from taking all important instructions from above builder
# taken python official docker image in that below version of alpine base image od
FROM python:3.9.23-alpine3.22
EXPOSE 8080
WORKDIR /opt/server
#Below inka, nenu optimaisations chestanu ana mata, like RUN , SYSTEM USER, 
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
#copying app code [build tool and build file concept ee ludu, Python lo Java laanti “build tool + build file” concept ledu. Endukante Python source code (.py) ni compile chesi jar laanti artifact create cheyyalsina avasaram ledu, interpreter direct ga run chestundi.]-> requirements.txt from builder
COPY --from=builder /opt/server /opt/server
#having error, while starting python conatiner[for uwsgi, so giving directly below command]
RUN apk add python3-dev build-base linux-headers pcre-dev
RUN pip3 install -r requirements.txt
# customised bridge network user
USER roboshop
#running the  app code in while payment conatiner starts, through CMD Instruction
CMD ["uwsgi","--ini","payment.ini"]


#********Multi stage builds *************


# FROM python:3.9
# # expose for documentation purpose only
# EXPOSE 8080

# WORKDIR /opt/server

# COPY requirements.txt .
# COPY *.py .
# COPY payment.ini .

# # runnnind and downloading dependencies.
# RUN pip3 install -r requirements.txt

# #running container -> bin[tarvatha nunchi cmd command lo add chestunnam , observe chesa, annai containers lo alage vunnai]
# CMD ["uwsgi","--ini","payment.ini"]