# basic web server
```go
func main() {
	svr := http.Server{
		Addr: ":80",
	}

	mux := http.NewServeMux()
	mux.Handle("/", http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
		_, _ = fmt.Fprint(w, "hello from go web server")
	}))
	svr.Handler = mux

	log.Fatal(svr.ListenAndServe())
}
```