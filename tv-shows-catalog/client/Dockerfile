FROM node:lts as builder

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

FROM node:lts

WORKDIR /app

COPY --from=builder /app/build ./build

COPY --from=builder /app/package*.json ./

COPY --from=builder /app/node_modules ./node_modules

CMD ["node", "build/index.js"]

