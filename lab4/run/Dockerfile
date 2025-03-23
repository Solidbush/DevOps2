FROM node:18-alpine AS run

WORKDIR /app/front
COPY --from=build /app/front/build ./build

WORKDIR /app/back
COPY --from=build /app/back/dist ./dist
COPY --from=build /app/back/node_modules ./node_modules

CMD ["node", "dist/main.js"]