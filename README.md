# lru-uasurfer
Golang LRU wrapping for [ua-surfer](https://github.com/avct/uasurfer).
## Use

### Instalation
```
	go get github.com/amonsat/lru-uasurfer
```
### Basic Use

```go
package main

import (
	"fmt"

	surfer "github.com/amonsat/lru-uasurfer"
)

func main() {
	s := surfer.New()
	s.LoadDump("")

	// This is an example how to use it
	r := s.Parse(`Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2486.0 Safari/537.36 Edge/13.10586`)

	// Print results
	fmt.Printf("Result: %#v \n", r)

	// if you want to dump cache, do it:
	s.SaveDump("")
}
```

### Benchmarks

origin uasurfer vs lruCache vs syncMap
```
BenchmarkParseUasurfer-4        1000000        1746 ns/op        142 B/op        1 allocs/op
BenchmarkParseLRU-4            10000000         172 ns/op          0 B/op        0 allocs/op
BenchmarkParseMap-4            20000000        77.6 ns/op          0 B/op        0 allocs/op
```
