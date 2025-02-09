# Install golang 1.16
FROM golang:1.16

EXPOSE 8080

WORKDIR /usr/src/app

# Copy all of the source code
COPY . .

# Build Project
RUN go build

# Test
RUN go test ./....

# Set Environmental variables
ENV REQUEST_ORIGIN=https://example.com

# Execute server file
CMD ["./server"]