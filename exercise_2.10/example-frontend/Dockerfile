# Ubuntu 22.04 as starting image 
FROM ubuntu:22.04

# Export port 5000
EXPOSE 5000

WORKDIR /usr/src/app

# Install curl and node
RUN apt-get update && apt-get -y install curl && \
    curl -sL https://deb.nodesource.com/setup_16.x | bash && \
    apt install -y nodejs && \
    node -v && npm -v

# Copy all of the source code
COPY . .

# Install all packages, Build static files for production mode and Install serve
RUN npm install && npm run build && npm install -g serve

# Set Environmental variables
# ENV REACT_APP_BACKEND_URL="http://localhost:8080"

# create the appuser and change the owner of current dir to appuser
RUN useradd -m appuser && chown appuser .  

# now we can change the user
USER appuser

# Run Application
CMD ["serve", "-s", "-l", "5000", "build"]