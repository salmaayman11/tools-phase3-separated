FROM node:18 

# Set the working directory
WORKDIR /usr/local/app

# Copy package.json and package-lock.json
COPY package.json package-lock.json ./

# Install dependencies
RUN npm install 

# Copy the rest of the application code
COPY . .
#comment
RUN chmod -R 777 /usr/local/app

# Expose port 4200
EXPOSE 4200


# Start the Angular application using npx
CMD ["npx", "ng", "serve", "--host", "0.0.0.0"]
