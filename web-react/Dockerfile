FROM node:alpine

ENV NPM_CONFIG_LOGLEVEL warn

# Create app folder and use it as the working directory
RUN mkdir -p /srv/app
WORKDIR /srv/app

COPY init/package.json /srv/app

RUN npm install

EXPOSE 3000

CMD ["npm", "start"]