FROM node:12-alpine as build
WORKDIR /app
COPY package*.json ./
RUN npm install -g @angular/cli@9.0.6 @angular-devkit/build-angular@0.900.6 && npm install
# RUN npm install
COPY . .
# RUN npm run build:prod
RUN npm run build

FROM httpd:2.4
RUN rm /usr/local/apache2/htdocs/index.html
COPY --from=build /app/dist/ /usr/local/apache2/htdocs/
EXPOSE 80


