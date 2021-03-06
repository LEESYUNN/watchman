
# Feature 特性

* 高性能。在 macbook pro 15 上测试，每个队列的处理能力可以轻松达到 3000 message/second 以上，多个队列也可以做到线性的增加性能，整体应用达到几万每秒很轻松。同时，得益于 golang 的协程设计，如果下游出现了慢调用，那么也不会影响并发。
* 优雅关闭。通过对信号的监听，整个程序可以在不丢消息的情况下优雅关闭，利于配置更改和程序重启。这个在生产环境非常重要。
* 自动重连。当 RabbitMQ 服务无法连接的时候，应用可以自动重连。

# Usage 使用

## Build
go build -o watchman

## Usage

```
Usage of ./watchman:
  -c string
        config file path (default "config/queues.example.yml")
  -log string
        logging file, default STDOUT
  -pidfile string
        If specified, write pid to file.
```

优雅关闭：
```
# kill -QUIT $PID
```

# config 配置
## ENV 文件
使用前需要先加载 env，样例见 config/env.example.yml，主要是 RabbitMQ 的配置。

## 队列配置文件
样例见 config/queues.example.yml, 主要是注明消息队列的配置以及回调地址和参数。

# Author 作者
大鱼（fishtrip.cn) 是国内领先的全球民宿平台，给用户提供全球特色的民宿、客栈、别墅等非标准住宿。目前公司的技术栈以 ruby 和 Java 为主，部分中间件采用 golang 编写。

# Licence 许可
MIT Licence
