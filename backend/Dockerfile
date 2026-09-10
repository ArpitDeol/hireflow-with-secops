FROM node:22-alpine AS builder

WORKDIR /app

RUN apk upgrade --no-cache

COPY package*.json ./

RUN npm ci --omit=dev

COPY . .


FROM node:22-alpine

WORKDIR /app

RUN apk upgrade --no-cache \
    && rm -rf /usr/local/lib/node_modules/npm \
    && rm -f /usr/local/bin/npm /usr/local/bin/npx

COPY --from=builder /app /app

EXPOSE 3000

CMD ["node", "src/server.js"]