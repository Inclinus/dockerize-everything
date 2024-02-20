FROM node:lts

WORKDIR /app

COPY . .

RUN npm install

RUN npm run build

CMD ["node", "build/index.js"]
