FROM ubuntu:latest

COPY --from=golang:latest /usr/local/go/ /usr/local/go/
COPY --from=golang:latest /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/
ENV PATH="/usr/local/go/bin:${PATH}"

RUN mkdir -p /app
WORKDIR /app


ENV GOPROXY=https://goproxy.cn,direct

COPY go.mod go.sum ./
RUN go mod download

COPY . .
RUN go build -o app main.go

ENTRYPOINT [ "bash" ]
