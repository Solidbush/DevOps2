FROM node:20-alpine AS builder

WORKDIR /app

RUN apk add --no-cache git \
    && git clone --depth 1 https://gitlab.com/deusops/projects/react-spring-app.git /repo \
    && mv /repo/react-frontend/* /app/ \
    && rm -rf /repo

ENV PUBLIC_URL=/

RUN npm ci && npm run build

FROM nginx:alpine

COPY --from=builder /app/build /usr/share/nginx/html

RUN chmod -R 755 /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]