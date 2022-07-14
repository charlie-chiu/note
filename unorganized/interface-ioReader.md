# interface io.Reader
```go
func main() {
	log.SetFlags(log.Lshortfile)
	readAll(strings.NewReader("Read reads up to len(buf) bytes into buf and returns the number of bytes read - it returns an io.EOF error when the stream ends."))
}

func readAll(reader io.Reader) {
	const n = 20

	buf := make([]byte, n)
	for {
		n, err := reader.Read(buf)

		log.Println(n, err, string(buf))

		if err == io.EOF {
			break
		}
	}
}

```
