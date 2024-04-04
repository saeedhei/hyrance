FROM node:20.9.0-alpine3.18 AS builder
WORKDIR /app
COPY package.json ./
RUN npm install
COPY . .
RUN npm run build


FROM nginx:stable-alpine AS runtime
COPY --from=builder /app/dist /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

# docker build -t hyrance-frontend .
# docker network create neto
# docker run --name front-container --network=neto -d -p 8080:80 hyrance-frontend