FROM node:latest

ENV NPM_CONFIG_LOGLEVEL warn
ENV SOURCE_CODE /srv/app

# Create app folder and use it as the working directory
RUN mkdir -p $SOURCE_CODE && chown node $SOURCE_CODE
WORKDIR $SOURCE_CODE

USER node
EXPOSE 3000

CMD ["npm", "start"]