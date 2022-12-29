# How to use


```
protoc --go-grpc_out=require_unimplemented_servers=false:./chatserver/ -go_out=./chatserver/ chat.proto
```

chat.pb.goと chat_grpc.go　がchatserverフォルダ内に自動生成される

## get started

```
go mod init gRPCChatServer
```

```
touch chat.proto
```

## create .proto file

``syntax = "proto3";

package chatserver;

// 1) Client to Server
message FromClient {

    string name = 1;
    string body = 2;
}

// 2) Server to Client
message FromServer {

    string name = 1;
    string body = 2; 
}

// Create RPC service named as ChatService
service Services {

    rpc ChatService(stream FromClient) returns (stream FromServer){};
}
```

## make directory for auto generated file

```
mkdir chatserver
```

Now, we have two files in the chatserver folder
- chat_grpc.pb.go
- chat.pb.go


## Creating gRPC server

```
touch server.go
```



#How to chat...

Terminalを開く (Server用)

```
env PORT=5000 go run server.go
```

Terminalをさらに２つ開く (Client用)

- 両方のTerminalで `client.go` を起動する

```
go run client.go
```

"YOUR NAME"にそれぞれのユーザー名を入力しチャット開始
