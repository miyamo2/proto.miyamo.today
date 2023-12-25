## blogproto

protobuf for simply blog application.

## Installation

```sh
git clone https://github.com/miyamo2/blogproto
```

as submodule

```sh
git submodule add https://github.com/miyamo2/blogproto
```

## Usage

### Building gRPC server

1. Initialize your repo & go module

```sh
mkdir myblog
cd ./myblog
git init
git submodule add https://github.com/miyamo2/blogproto proto
go mod init myblog
```

2. Setup protoc-gen-go

```sh
go install google.golang.org/grpc@latest
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest
```

3. Generate Message & Service.

```sh
cd ./proto
protoc --go_out=../pb --go_opt=paths=source_relative \
 --go-grpc_out=../pb --go-grpc_opt=paths=source_relative \
 article.proto
```
