# Ubuntu 22.04 as starting image 
FROM ubuntu:22.04

# Export port 5000
EXPOSE 5000

WORKDIR /usr/src/app

# Install curl
RUN apt-get update && apt-get -y install curl

# Install node
RUN curl -sL https://deb.nodesource.com/setup_16.x | bash
RUN apt install -y nodejs

# Verify node and npm versions
RUN node -v && npm -v

# Copy all of the source code
COPY . .

# Install all packages
RUN npm install 

# Build static files for production mode
RUN npm run build

# Install serve
RUN npm install -g serve

# Run Application
CMD ["serve", "-s", "-l", "5000", "build"]