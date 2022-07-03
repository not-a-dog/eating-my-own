FROM ubuntu:latest

COPY --from=golang:latest /usr/local/go/ /usr/local/go/
ENV PATH="/usr/local/go/bin:${PATH}"

RUN mkdir -p /app
WORKDIR /app

COPY go.mod .
RUN go mod download

COPY . .
RUN go build -o main main.go

ENTRYPOINT [ "bash" ]
