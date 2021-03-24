FROM node:current-alpine

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

#ENV PORT 5000
#the route to the url es defined in docker-compose 
#ENV MONGO_URL "mongodb://mongo:27017"

EXPOSE 5000

CMD ["npm","start"]

