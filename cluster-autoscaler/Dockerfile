FROM golang:latest AS builder

WORKDIR /
COPY go.mod go.sum ./
RUN go mod download
COPY . .
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o cluster-autoscaler main.go

FROM alpine
WORKDIR /

COPY --from=builder /cluster-autoscaler cluster-autoscaler

RUN chmod +x /cluster-autoscaler
ENTRYPOINT ["./cluster-autoscaler"]