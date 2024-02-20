# Créer un Dockerfile pour cette application en mode production
FROM node:lts

EXPOSE 3000

WORKDIR /app

COPY . .

RUN npm install

RUN npm run build

CMD ["node", "dist/main.js"]
