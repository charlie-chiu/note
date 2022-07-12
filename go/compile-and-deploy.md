# Cross Compiling 交叉編譯
## To MacOs
```sh
CGO_ENABLED=0 GOOS=darwin GOARCH=amd64 go build main.go
```

## To Linux (alpine)
```sh
CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build main.go
```

# references
[Docker Hub](https://hub.docker.com/_/golang)
[使用 Go 运行与部署 - 知乎](https://zhuanlan.zhihu.com/p/91587465)
