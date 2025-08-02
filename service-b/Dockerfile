FROM golang:1.23 as builder

WORKDIR /app
COPY . .
RUN go mod download
RUN CGO_ENABLED=0 GOOS=linux go build -o service-b .

FROM alpine:latest
WORKDIR /app
COPY --from=builder /app/service-b .
ENV WEATHER_API_KEY=82a06c268ded479ca51163545251407
EXPOSE 8081
CMD ["./service-b"]