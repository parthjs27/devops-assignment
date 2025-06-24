# -------- Build Stage --------
FROM golang:1.24.4-bullseye AS builder

WORKDIR /app

COPY go.mod .
COPY main.go .

# Build a static binary to avoid glibc dependency issues
RUN CGO_ENABLED=0 GOOS=linux go build -o service1

# -------- Run Stage --------
FROM debian:bullseye-slim

WORKDIR /app

COPY --from=builder /app/service1 .

EXPOSE 8001

CMD ["./service1"]
