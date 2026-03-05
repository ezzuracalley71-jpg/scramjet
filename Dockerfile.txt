FROM node:22-alpine

RUN npm install -g pnpm

WORKDIR /app

COPY package.json ./

RUN pnpm install --no-frozen-lockfile

COPY . .

RUN pnpm run build

EXPOSE 8080

CMD ["node", "server.js"]
