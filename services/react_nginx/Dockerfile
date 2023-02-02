# first building react project, using node base image
FROM node:16 as build

# setting working dir inside container
WORKDIR /usr/src/front

# required to install packages
COPY package.json /usr/src/front

# installing npm packages
RUN npm install --legacy-peer-deps

# copying over react source material
COPY src /usr/src/front/src

# copying over further react material
COPY public /usr/src/front/public

# creating production build to serve through nginx
RUN npm install -g serve
RUN npm run build

# Deploy react app, using nginx base image
FROM nginx:1.15.8

RUN rm /etc/nginx/conf.d/default.conf
COPY certificate.crt /etc/nginx/certs/nginx-selfsigned.crt
COPY privateKey.key /etc/nginx/certs/nginx-selfsigned.key
COPY --from=build /usr/src/front/build/ /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d