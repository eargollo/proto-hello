# Protobuf Hello Tuturial

Following tutorial from https://grpc-ecosystem.github.io/grpc-gateway/docs/tutorials/introduction/

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