FROM node:18-alpine

WORKDIR /usr/src/app

COPY package.json yarn.lock ./

RUN yarn install

COPY . .

EXPOSE 5000

CMD ["node", "src/app.js"]