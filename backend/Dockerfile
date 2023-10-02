FROM node:13.12.0-alpine

# Set the working directory and copy package.json and package-lock.json separately
WORKDIR /app
COPY package*.json ./

# Install dependencies and remove unnecessary cache
RUN npm install && \
    npm cache clean --force && \
    rm -rf /tmp/*

# Copy the rest of the application code
COPY . .

# Start the application
CMD [ "npm", "start" ]
