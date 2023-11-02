FROM node:18-slim as prod
ENV NODE_ENV=production
WORKDIR /app

# this wasn't in the starter Dockerfile, but in the www.js file I saw it uses port 300
EXPOSE 3000

# pull in the package.json and package-lock.json, and do a production npm install
COPY package*.json ./
RUN npm ci && npm cache clean --force

COPY . .

CMD ["node", "./bin/www"]

FROM prod as dev
ENV NODE_ENV=development

# install the devDependencies
RUN npm install && npm cache clean --force
CMD ["nodemon", "./bin/www", "--inspect=0.0.0.0:9229"]

FROM dev as test
ENV NODE_ENV=development

CMD ["npm", "test"]