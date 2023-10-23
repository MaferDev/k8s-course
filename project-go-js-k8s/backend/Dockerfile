FROM golang:1.17 as builder

# Set destination for COPY
WORKDIR /app

COPY ./src/main.go .

# Build
RUN CGO_ENABLED=0 GOOS=linux GOPROXY=https://proxy.golang.org go build -o app ./main.go

FROM alpine:latest

WORKDIR /app
COPY --from=builder /app/app .
ENTRYPOINT ["./app"]