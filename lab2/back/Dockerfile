FROM node:21-alpine

WORKDIR /usr/src/app

RUN apk add --no-cache python3 make g++

COPY package*.json ./

RUN npm ci && npm rebuild bcrypt --build-from-source && npm cache clean --force

COPY . .

COPY entrypoint.sh /usr/local/bin/entrypoint.sh
RUN chmod +x /usr/local/bin/entrypoint.sh

RUN addgroup -S appgroup && adduser -S appuser -G appgroup

RUN mkdir -p /usr/src/app/dist && chown -R appuser:appgroup /usr/src/app

USER appuser

EXPOSE 5000

ENTRYPOINT ["entrypoint.sh"]
CMD ["npm", "run", "start"]