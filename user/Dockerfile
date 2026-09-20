## fourth time we make change layers for build time decrease speed increases
FROM node:20.20.2-alpine3.22 AS builder
WORKDIR /app
COPY package.json .
COPY *.js .
RUN npm install


FROM node:20.20.2-alpine3.22
WORKDIR /app
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S -G roboshop roboshop && \
    chown -R roboshop:roboshop /app
COPY --from=builder /app /app/
USER roboshop
CMD ["node", "server.js"]


##Third time we add user acess for container not root access
# FROM node:20.20.2-alpine3.22 AS builder
# WORKDIR /app
# COPY *.js .
# COPY package.json .
# RUN npm install


# FROM node:20.20.2-alpine3.22 
# WORKDIR /app
# #we can add user to run our container as user acces not root access
# RUN addgroup -S roboshop && adduser -S -G roboshop roboshop && \  
#     chown -R roboshop:roboshop /app
# COPY --from=builder /app /app  
# EXPOSE 8080
# USER roboshop
# CMD [ "node","server.js" ]




###second time we change os so size is reduce by os 500mb by adding os  node:20.20.2-alpine3.22 and also   multistage blocks from used
# FROM node:20.20.2-alpine3.22 AS builder   #this runs at buildtime
# WORKDIR /app
# COPY *.js .
# COPY package.json .
# RUN npm install


# FROM node:20.20.2-alpine3.22  #this runs at run time
# WORKDIR /app
# COPY --from=builder /app /app  
# EXPOSE 8080 
# CMD [ "node","server.js" ]


#### First time running code as size nodeis 1.40GB
# FROM node:20
# WORKDIR /app
# COPY *.js .
# COPY package.json .
# RUN npm install
# CMD [ "node","server.js" ]