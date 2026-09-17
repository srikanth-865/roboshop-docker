
FROM node:20.20.2-alpine3.22 AS builder
WORKDIR /app
COPY *.js .
COPY package.json .
RUN npm install


FROM node:20.20.2-alpine3.22 
WORKDIR /app
RUN addgroup -S roboshop && adduser -S -G roboshop roboshop && \
    chown -R roboshop:roboshop /app
EXPOSE 8080
ENV MONGO=true \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
RUN addgroup -S roboshop && adduser -S -G roboshop roboshop && \
    chown -R roboshop:roboshop /app
#if developer changes any code so it build again so we put at top so no disturbances for next layer
COPY --from=builder /app /app  
USER roboshop
CMD [ "node","server.js" ]

















# FROM node:20.20.2-alpine3.22 AS builder
# WORKDIR /app
# COPY *.js .
# COPY package.json .
# RUN npm install
# ENV MONGO=true \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"

# FROM node:20.20.2-alpine3.22 
# WORKDIR /app
# #we can add user to run our container as user acces not root access
# RUN addgroup -S roboshop && adduser -S -G roboshop roboshop && \  
#     chown -R roboshop:roboshop /app
# COPY --from=builder /app /app  
# EXPOSE 8080
# ENV MONGO=true \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# USER roboshop
# CMD [ "node","server.js" ]












# FROM node:20.20.2-alpine3.22 AS builder
# WORKDIR /app
# COPY *.js .
# COPY package.json .
# RUN npm install
# ENV MONGO=true \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"

# FROM node:20.20.2-alpine3.22 
# WORKDIR /app
# COPY --from=builder /app /app  
# EXPOSE 8080
# ENV MONGO=true \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD [ "node","server.js" ]









# FROM node:20
# WORKDIR /app
# COPY *.js .
# COPY package.json .
# RUN npm install
# ENV MONGO=true \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD [ "node","server.js" ]