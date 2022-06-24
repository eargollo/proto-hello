# Protobuf Hello Tuturial

Following tutorial from https://grpc-ecosystem.github.io/grpc-gateway/docs/tutorials/introduction/

## Comments

- Got error on tutorial not having a go _package.
- To generate code: `buf generate`
- Curl: `grpcurl -v -plaintext -d '{"name": "abacaxi"}' localhost:8080 helloworld.Greeter/SayHello`