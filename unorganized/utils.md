Go 版本的 var_dump

```go
func Dump(args ...interface{}) {
	pc, file, line, ok := runtime.Caller(1)
	if ok {
		fmt.Printf("%s:%d in %s\n", file, line, runtime.FuncForPC(pc).Name())
	}

	for _, arg := range args {
		fmt.Printf("(%T) %v\n", arg, arg)
	}
}

func DumpType(args ...interface{}) {
	for _, arg := range args {
		typeOf := reflect.TypeOf(arg)
		fmt.Printf("(Type : %T / Name : %s / Kind : %s) %v\n", arg, typeOf.Name(), typeOf.Kind(), arg)
	}
}
```