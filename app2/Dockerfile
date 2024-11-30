# Stage 1: Build
FROM golang:1.19 AS builder
WORKDIR /app
COPY go.mod ./
RUN go mod download
COPY . .
RUN go build -o app2 .

# Stage 2: Runtime
FROM gcr.io/distroless/base-debian11
WORKDIR /
COPY --from=builder /app/app2 /
CMD ["/app2"]