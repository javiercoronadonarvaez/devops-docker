# Install golang 1.16
FROM golang:1.16

EXPOSE 8080

WORKDIR /usr/src/app

# Copy all of the source code
COPY . .

# Set Environmental variables
# ENV REQUEST_ORIGIN="http://localhost:3000"

# Build Project
RUN go build

# Test
RUN go test ./....

# create the appuser
RUN useradd -m appuser

# change the owner of current dir to appuser
RUN chown appuser .

# now we can change the user
USER appuser

# Execute server file
CMD ["./server"]