FROM node:alpine

# Copy package.json and package-lock.json to the image
# We need them to build the dependencies for our project
RUN npm i npm@latest -g
COPY package.json package.json
COPY package-lock.json package-lock.json

# Run `npm ci` to install project dependencies
RUN npm ci

# Install @vis.gl/react-google-maps and @googlemaps/markerclusterer
RUN npm install @vis.gl/react-google-maps @googlemaps/markerclusterer
RUN npm install framer-motion

# Set environment variables
ENV CI=true
ENV PORT=3000

# Copy the entire project directory to the image
COPY . .

# Default command to start the app
CMD [ "npm", "start" ]
