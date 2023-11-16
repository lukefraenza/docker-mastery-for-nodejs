FROM node:14-slim

# Set the working directory to the application directory
WORKDIR /app

# install graphicsmagick
RUN apt-get update \
    && apt-get install -y graphicsmagick

# pull in the package.json and package-lock.json, and do a production npm install
COPY package*.json ./
RUN npm install \
    && npm cache clean --force

# Add your application files to the container
COPY . .

# Start the application
CMD ["node", "./index.js"]
