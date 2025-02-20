# Step 1: Build the binary using a Go alpine image
FROM golang:1.24-alpine3.21 AS builder

WORKDIR /usr/src/app

# Copy source code
COPY . .

# Build the binary as a small static executable
RUN CGO_ENABLED=0 GOOS=linux go build -ldflags="-s -w" -o server . 

# Create a non-root user (appuser) in the builder stage
RUN adduser -D -g '' appuser

# Step 2: Use scratch as the final base image
FROM scratch

WORKDIR /root/

# Copy the compiled Go binary from the builder stage with correct permissions
COPY --from=builder /usr/src/app/server .
COPY --from=builder /etc/passwd /etc/passwd 

# Switch to non-root user
USER appuser

# Expose the backend port
EXPOSE 8080

# Run the server
CMD ["./server"]
