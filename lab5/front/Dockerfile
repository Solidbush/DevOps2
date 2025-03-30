FROM node:alpine

WORKDIR /app

RUN apk add --no-cache git

RUN git clone --depth 1 https://gitlab.com/deusops/projects/react-spring-app.git /app/repo \
    && mv /app/repo/react-frontend/* /app/ \
    && rm -rf /app/repo \
    && apk del git

RUN ls -la package.json package-lock.json

RUN npm ci \
    && npm cache clean --force

USER node

CMD ["npm", "start"]