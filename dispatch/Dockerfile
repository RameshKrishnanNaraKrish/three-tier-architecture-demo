# Use the latest Go version
FROM golang:1.18 AS builder

WORKDIR /go/src/app

# Copy the Go files
COPY *.go . 

# Initialize module and download dependencies
RUN go mod init dispatch && go mod tidy

# Build the application
RUN go build -o dispatch .

# Final stage
FROM alpine:latest

WORKDIR /root/

# Copy the binary from the builder stage
COPY --from=builder /go/src/app/dispatch .

# Command to run the binary
CMD ["./dispatch"]
