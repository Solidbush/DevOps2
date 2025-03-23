FROM system AS build

WORKDIR /app/front
COPY front/package.json front/package-lock.json ./
RUN npm ci --only=production
COPY front ./
RUN npm run build

WORKDIR /app/back
COPY back/package.json back/package-lock.json ./
RUN npm ci --only=production
COPY back ./
RUN npm run build