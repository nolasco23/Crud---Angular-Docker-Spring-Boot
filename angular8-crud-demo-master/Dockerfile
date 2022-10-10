FROM node:14.15.0 as builder

RUN mkdir -p /app

WORKDIR /app

# COPY package.json .

# RUN npm cache clean
COPY . .

RUN npm install @angular/cli -g
RUN npm i --force
RUN ng build


FROM nginx:alpine
COPY src/nginx/etc/conf.d/default.conf /etc/nginx/conf/default.conf
COPY --from=builder app/dist/angular8-crud-demo usr/share/nginx/html

# CMD ["npm", "start"]
