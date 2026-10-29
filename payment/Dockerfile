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
#copying app code and build file-> requirements.txt from builder
COPY --from=builder /opt/server /opt/server
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