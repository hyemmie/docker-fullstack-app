FROM node:alpine as builder
WORKDIR /app
COPY package.json ./
RUN npm install
COPY ./ ./
RUN npm run build

# 운영 환경에는 개발 서버가 없기 때문에 nginx로 대체해야 함
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html