FROM golang:1.21 AS builder

WORKDIR /app
COPY . .

RUN go mod download
RUN CGO_ENABLED=0 GOOS=linux go build -o broadcaster main.go

FROM alpine:latest
WORKDIR /app
COPY --from=builder /app/broadcaster .

ENV APP_KEY=""
ENV APP_SECRET=""
ENV ACCESS_TOKEN=""

ENTRYPOINT ["./broadcaster"]