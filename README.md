# goでweb作る

以下を参考にやってみた
https://astaxie.gitbooks.io/build-web-application-with-golang/content/ja/01.2.html
https://iij.github.io/bootcamp/server-app/go/#_0-4-%E6%9C%AC%E8%B3%87%E6%96%99%E3%81%AE%E8%A1%A8%E7%8F%BE

# command history

gopath以下じゃなくても、goを動かせるようになってる

```
8210  go mod init firstgo_app
 8212  cat go.mod
 8213  echo 'package main\nimport "github.com/gin-gonic/gin"\nfunc main() {\n        r := gin.Default()\n        r.GET("/ping", func(c *gin.Context) {\n                c.JSON(200, gin.H{\n                        "message": "pong",\n                })\n        })\n        r.Run() // listen and serve on 0.0.0.0:8080\n}' > main.go\n
 8215  cat main.go
 8216  go build
 8218  cat go.sum
 8220  echo 'package handlers\nimport "github.com/gin-gonic/gin"\nfunc Ping(c *gin.Context) {\n    c.JSON(200, gin.H{\n        "message": "pong",\n    })\n}' > handlers/ping.go
 8222  echo 'package handlers\nimport "github.com/gin-gonic/gin"\nfunc Ping(c *gin.Context) {\n    c.JSON(200, gin.H{\n        "message": "pong",\n    })\n}' > handlers/ping.go
 8224  echo 'package main\nimport (\n    "firstgo_app/handlers"\n    \n    "github.com/gin-gonic/gin"\n)\nfunc main() {\n        r := gin.Default()\n        r.GET("/ping", handlers.Ping)\n        r.Run() // listen and serve on 0.0.0.0:8080\n}' > main.go
 8227  cat main.go
 8229  ./firstgo_app
```

でcurl

```
➜  ~ curl localhost:8080
404 page not found%
➜  ~ curl localhost:8080/ping
{"message":"pong"}%
```
