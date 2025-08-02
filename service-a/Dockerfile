FROM golang:1.23 as builder

WORKDIR /app
COPY . .
RUN go mod download
RUN CGO_ENABLED=0 GOOS=linux go build -o service-a .

FROM alpine:latest
WORKDIR /app
COPY --from=builder /app/service-a .
EXPOSE 8080
CMD ["./service-a"]