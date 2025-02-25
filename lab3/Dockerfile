FROM node:20-alpine AS build

WORKDIR /app
COPY package.json package-lock.json ./
RUN npm ci --omit=dev && npm cache clean --force

COPY . .
RUN npm run build

FROM nginx:alpine

RUN addgroup -S appgroup && adduser -S appuser -G appgroup

RUN mkdir -p /var/cache/nginx/client_temp /tmp/nginx_temp/proxy && \
    chown -R appuser:appgroup /var/cache/nginx /tmp/nginx_temp

COPY nginx.conf /etc/nginx/nginx.conf

USER appuser

COPY --from=build /app/build /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
