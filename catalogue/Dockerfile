
FROM node:20.20.2-alpine3.22 AS builder
WORKDIR /app
COPY *.js .
COPY package.json .
RUN npm install
ENV MONGO=true \
    MONGO_URL="mongodb://mongodb:27017/catalogue"

FROM node:20.20.2-alpine3.22 
WORKDIR /app
COPY --from=builder /app /app  
EXPOSE 8080
ENV MONGO=true \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
CMD [ "node","server.js" ]












# FROM node:20.20.2-alpine3.22 AS builder
# WORKDIR /app
# COPY *.js .
# COPY package.json .
# RUN npm install
# ENV MONGO=true \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD [ "node","server.js" ]

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