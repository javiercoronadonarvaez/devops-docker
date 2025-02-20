# Install golang 1.16
FROM golang:1.24-alpine3.21

EXPOSE 8080

WORKDIR /usr/src/app

# Copy all of the source code
COPY . .

# Set Environmental variables
# ENV REQUEST_ORIGIN="http://localhost:3000"

# Build Project and Test
RUN go build && go test ./....

# create the appuser and change the owner of current dir to appuser
RUN adduser -D -g '' appuser && chown appuser .

# now we can change the user
USER appuser

# Execute server file
CMD ["./server"]