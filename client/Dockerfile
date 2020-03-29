FROM node:alpine AS builder
WORKDIR '/app'
COPY package.json ./
RUN npm install
COPY . .
RUN npm run build
# this creatse a /build folder of assets, need to copy that to our nginx server

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html