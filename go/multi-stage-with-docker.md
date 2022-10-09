build Golang binary from a image, then copy binary to alpine image to reduce image size.


```dockerfile
FROM golang:1.18-alpine AS builder

WORKDIR /go/src/app

COPY . /go/src/app

CMD ["echo", "$PWD"]

RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -v -o /go/bin/app ./cmd/api

FROM alpine:3.14.8 as release

COPY --from=builder /go/bin/app /opt

ENTRYPOINT /opt/app
```
