FROM python:3.9
WORKDIR /app
COPY payment.ini .
COPY payment.py . 
COPY rabbitmq.py  . 
COPY requirements.txt .
RUN pip3 install -r requirements.txt
EXPOSE 8080
CMD ["uwsgi", "--ini", "payment.ini"]