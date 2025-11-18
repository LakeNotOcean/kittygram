FROM node:25-alpine

WORKDIR /app

COPY package.json package.json
COPY package-lock.json package-lock.json

RUN npm ci

COPY . .
RUN npm run build
RUN npm install --global http-server

# Пользователь сервиса
RUN useradd -m -r appuser && chown -R appuser /app
USER appuser

CMD ["npx", "-y", "http-server", "-p", "3000", "/app/build"]
