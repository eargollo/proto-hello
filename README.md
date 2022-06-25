# Protobuf Hello Tuturial

Following tutorial from https://grpc-ecosystem.github.io/grpc-gateway/docs/tutorials/introduction/

## Building

### Generating protobuf files 

This step is only needed if the `.proto` files are changed. All generated files are at the `gen` path.

Generating files:
```
buf generate
```

### Compiling

```
go build . 
```

### Testing

First test the gRPC endpoints. Run the program at another terminal `go run .`  

```
# List endpoints
$ grpcurl -plaintext localhost:8080 list
grpc.reflection.v1alpha.ServerReflection
helloworld.Greeter

# Call SayHello
$ grpcurl -plaintext -d '{"name":"Hello"}' localhost:8080 helloworld.Greeter/SayHello
{
  "message": "Hello world"
}
```

Now let's test the REST endpoint
```
# Test the post endpoint
$ $ curl -d '{"name":"Hello"}' localhost:8090/v1/example/hello
{"message":"Hello world"}

# Test the get endpoint
$ curl  localhost:8090/v1/example/hello/hello
{"message":"hello world (GET)"}
```

## Comments

- Got error on tutorial not having a go _package.
- To generate code: `buf generate`
- Curl: `grpcurl -plaintext -d '{"name": "abacaxi"}' localhost:8080 helloworld.Greeter/SayHello`
- List: `grpcurl -plaintext localhost:8080 list`


protoc -I ./proto  -I ./ \
  --go_out ./gen/proto --go_opt paths=source_relative \
  --go-grpc_out ./gen/proto --go-grpc_opt paths=source_relative \
  --grpc-gateway_out ./gen/proto --grpc-gateway_opt paths=source_relative \
  ./proto/helloworld/hello_world.proto