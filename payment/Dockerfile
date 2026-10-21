FROM python:3.9
# expose for documentation purpose only
EXPOSE 8080

WORKDIR /opt/server

COPY requirements.txt .
COPY *.py .
COPY payment.ini .

# runnnind and downloading dependencies.
RUN pip3 install -r requirements.txt

#running container -> bin[tarvatha nunchi cmd command lo add chestunnam , observe chesa, annai containers lo alage vunnai]
CMD ["uwsgi","--ini","payment.ini"]