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

# Execute server file
CMD ["./server"]