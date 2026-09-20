#Build Stage
FROM python:3.9.25-alpine3.22 AS builder
WORKDIR /app
#installing all python libraries/dependencies to inside /install directory from requirements.txt
COPY  requirements.txt .
#Here apk is the Alpine Linux package manager.Some Python libraries need to be compiled while being installed.
RUN apk add --no-cache --virtual .build-deps gcc musl-dev linux-headers python3-dev \
    && pip3 install --prefix=/install -r requirements.txt \
    && apk del .build-deps

#This creates a new final image,final image does not automatically contain everything from the builder stage.That's why we explicitly copy what we need.
FROM python:3.9.25-alpine3.22
WORKDIR /app
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S -G roboshop roboshop && \
    chown -R roboshop:roboshop /app
#From the builder stage, taking from /install and copy it into /usr/local in the final image.
COPY  --from=builder /install /usr/local
#changes ownership of /app to that user/group to our roboshop 
COPY --chown=roboshop:roboshop payment.ini *.py requirements.txt  ./
USER roboshop
#Read the configuration from payment.ini and start the application according to that configuration.
CMD ["uwsgi", "--ini", "payment.ini"]







##First time runnning
# FROM python:3.9
# WORKDIR /app
# COPY payment.ini .
# COPY payment.py . 
# COPY rabbitmq.py  . 
# COPY requirements.txt .
# RUN pip3 install -r requirements.txt
# EXPOSE 8080
# CMD ["uwsgi", "--ini", "payment.ini"]