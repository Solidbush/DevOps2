FROM node:18-alpine AS system

RUN apk add --no-cache bash && rm -rf /var/cache/apk/*

RUN addgroup -S appgroup && adduser -S appuser -G appgroup
USER appuser