# variable
```
& 取址
* 取值

p := &i         // point to i
fmt.Println(*p) // read i through the pointer
*p = 21         // set i through the pointer
fmt.Println(i)  // see the new value of i

p = &j         // point to j
*p = *p / 37   // divide j through the pointer
fmt.Println(j) // see the new value of j
```

# type
The type *T is a pointer to a T

# function declare
```go
func (v value, p *pointer) {
    //...
} 
```


