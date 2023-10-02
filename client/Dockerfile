FROM node:13.12.0-alpine

# Create the app directory and set it as the working directory
WORKDIR /app

# Copy package.json and package-lock.json first and install dependencies
COPY package*.json ./
RUN npm install && npm cache clean --force

# Copy the application code
COPY . .

# Start the application
CMD [ "npm", "start" ]