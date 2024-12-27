# Use a lightweight Node.js base image for building the Angular app
FROM node:18-alpine AS build

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json to leverage Docker caching
COPY package*.json ./

# Install dependencies (cached layer)
RUN npm install --legacy-peer-deps

# Copy only the application source files
COPY src ./src
COPY angular.json ./
COPY tsconfig*.json ./

# Build the Angular app for production
RUN npm run build -- --output-path=dist

# Use the official NGINX base image for serving
FROM nginx:stable-alpine
COPY ./nginx.conf /etc/nginx/nginx.conf
COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 8080
USER nginx
CMD ["nginx", "-g", "daemon off;"]
