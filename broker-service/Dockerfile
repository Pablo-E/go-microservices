# base go image
FROM golang:1.18-alpine as builder

RUN mkdir /app

WORKDIR /app

COPY . /app

RUN CGO_ENABLE=0 go build -o brokerApp ./cmd/api

RUN chmod +x /app/brokerApp

# build a tiny docker image
FROM alpine:latest

RUN mkdir /app

WORKDIR /app

COPY --from=builder /app/brokerApp /app

EXPOSE 8080

CMD [ "/app/brokerApp"]