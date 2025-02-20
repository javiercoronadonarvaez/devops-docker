# Use an official Node.js image
FROM node:16-alpine3.16

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
RUN npm run build && npm install -g serve

# Create the appuser and change ownership
RUN adduser -D -g '' appuser && chown -R appuser /usr/src/app

# Switch to the non-root user
USER appuser

# Run the application
CMD ["serve", "-s", "-l", "5000", "build"]
