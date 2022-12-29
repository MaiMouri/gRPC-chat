# How to


```
protoc --go-grpc_out=require_unimplemented_servers=false:./chatserver/ -go_out=./chatserver/ chat.proto
```

chat.pb.goと chat_grpc.go　がchatserverフォルダ内に自動生成される

