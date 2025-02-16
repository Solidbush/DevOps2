FROM node:21-alpine

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install && npm cache clean --force

COPY . .

RUN npm run build

RUN npm install -g serve

RUN npm install -g serve && npm cache clean --force

RUN addgroup -S appgroup && adduser -S appuser -G appgroup

USER appuser

CMD ["serve", "-s", "build", "-l", "4000"]