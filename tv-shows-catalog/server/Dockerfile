# Créer un Dockerfile pour cette application en mode production

FROM node:lts

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

RUN npm run build
EXPOSE 3000

CMD ["node", "dist/main.js"]