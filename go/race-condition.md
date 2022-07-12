Run with race condition test
```shell
go run -race main.go
```
Can use `-race` with go build too, just use it!

Test with
```shell
go test -v -run TestClient/register_on_connect_and_unregister_on_disconnect -race 
```

# references
[Data races in Go(Golang) and how to fix them 🏃‍♀️ - Soham's blog](https://www.sohamkamani.com/blog/2018/02/18/golang-data-race-and-how-to-fix-it/)
[MutexOrChannel · golang/go Wiki · GitHub](https://github.com/golang/go/wiki/MutexOrChannel)

