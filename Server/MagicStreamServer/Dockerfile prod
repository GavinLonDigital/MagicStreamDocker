FROM golang:1.24-alpine AS build

WORKDIR /app

# Copy dependency files first
COPY go.mod go.sum ./
RUN go mod download

# Now copy full source
COPY . .

# Build binary
RUN go build -o api-golang

# Production stage
FROM alpine:latest

WORKDIR /app
COPY --from=build /app/api-golang .

EXPOSE 8080
CMD ["./api-golang"]

# Goal	Best Image
# Smallest production image	Multi-stage → golang:1.22-alpine → scratch
# Secure & lightweight	golang:1.22-alpine
# Fastest CI builds	golang:1.22

# Why?

# Final image size is usually 5–15 MB

# Zero attack surface

# FROM golang

# WORKDIR /app

# COPY . .

# RUN go mod download

# RUN go build -o api-golang

# EXPOSE 8080

# CMD ["./api-golang"]
