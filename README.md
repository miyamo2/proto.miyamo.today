## proto.miyamo.today

protobuf for simply blog application.

## Installation

```sh
git clone https://github.com/miyamo2/proto.miyamo.today
```

as submodule

```sh
git submodule add https://github.com/miyamo2/proto.miyamo.today
```

## Usage

### Building gRPC server

1. Initialize your repo & go module.

```sh
mkdir myblog
cd ./myblog
git init
git submodule add https://github.com/miyamo2/proto.miyamo.today proto
go mod init myblog
```

2. Setup protoc-gen-go.

```sh
go install google.golang.org/grpc@latest
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest
```

3. Generate message & service.

```sh
protoc --proto_path=./proto/article --go_out=. --go_opt=Marticle.proto=internal/pb --go-grpc_out=. --go-grpc_opt=Marticle.proto=internal/pb ./proto/article/article.proto
protoc --proto_path=./proto/tag --go_out=. --go_opt=Mtag.proto=internal/pb --go-grpc_out=. --go-grpc_opt=Mtag.proto=internal/pb ./proto/tag/tag.proto
protoc --proto_path=./proto/blogging_event --go_out=. --go_opt=Mblogging_event.proto=internal/pb --go-grpc_out=. --go-grpc_opt=Mblogging_event.proto=internal/pb ./proto/blogging_event/blogging_event.proto
```
