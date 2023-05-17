FROM node:16 as build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm install -g @angular/cli build


FROM nginx

COPY --from=build /app/build /var/www/html
COPY ./default.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
EXPOSE 443
CMD ["nginx","-g","daemon off;"]