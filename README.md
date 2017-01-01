# HTTP Client

This plugin is a http client for go-micro.

The http client wraps net/http to provide a robust go-micro client with service discovery, load balancing and streaming.
It complies with the [go-micro.Client](https://godoc.org/github.com/micro/go-micro/client#Client) interface.

## Usage

### Use directly

```go
import "github.com/micro/go-plugins/client/http"

service := micro.NewService(
	micro.Name("my.service"),
	micro.Client(http.NewClient()),
)
```

### Use with flags

```go
import _ "github.com/micro/go-plugins/client/http"
```

```shell
go run main.go --client=http
```

### Call Service

Assuming you have a http service "my.service" with path "/foo/bar"
```go
// new client
client := http.NewClient()

// create request/response
request := client.NewRequest("my.service", "/foo/bar", &proto.Request{})
response := new(proto.Response)

// call service
err := client.Call(context.TODO(), request, response)
```

Look at http_test.go for detailed use.
