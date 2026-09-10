FROM node:22-alpine

WORKDIR /app

RUN apk upgrade --no-cache

# Update npm bundled with Node image
RUN npm install -g npm@latest

COPY package*.json ./

RUN npm ci --omit=dev

COPY . .

EXPOSE 3000

CMD ["npm", "start"]