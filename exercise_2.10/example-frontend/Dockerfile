# Use an official Node.js image and implement it as build-stage
FROM node:16-alpine3.16 as build-stage

# Expose port 5000
EXPOSE 5000

# Set working directory
WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package.json package-lock.json ./

# Install build dependencies (only for Alpine)
RUN apk add --no-cache python3 make g++

# Install dependencies with unsafe permissions
RUN npm install --unsafe-perm

# Copy the rest of the application
COPY . .

# Build static files
RUN npm run build 

# Use an official Node.js image 
FROM node:16-alpine3.16 

# Install serve
RUN npm install -g serve

# Create the appuser and change ownership
RUN adduser -D -g '' appuser 

# Copy built assets from build-stage
COPY --from=build-stage /usr/src/app/build build

# Change ownership of the copied files
RUN chown -R appuser build

# Switch to the non-root user
USER appuser

# Run the application
CMD ["serve", "-s", "-l", "5000", "build"]