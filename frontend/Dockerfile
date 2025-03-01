# Base image for building
FROM node:12 AS builder

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json 
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the remaining code
COPY . .

# Copy .env file
ENV  AUTH_API_ADDRESS=${AUTH_API_ADDRESS} \
    TODOS_API_ADDRESS=${TODOS_API_ADDRESS}

# Build the application
RUN npm run build

# Using Nginx to serve the built files
FROM nginx:alpine

# Copy the built app from the builder stage to nginx's web directory
COPY --from=builder /app/dist /usr/share/nginx/html
COPY nginx.conf /etc/nginx/nginx.conf

# Expose port 80
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
