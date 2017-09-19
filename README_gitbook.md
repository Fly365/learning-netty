# Netty学习笔记

Netty学习笔记, 包括代码学习, 源码分析.基于netty4.1, 用于记录Netty学习过程的各种信息和心得.

## Netty的代码结构

netty源码的组织结构和包含的package如下：

1. common
	- `io.netty.util`
	- `io.netty.util.concurrent`
1. resolver
	- `io.netty.resolver`
1. resolver-dns
	- `io.netty.resolver.dns`
1. buffer
	- `io.netty.buffer`
1. transport
	- `io.netty.bootstrap`
	- `io.netty.channel`
	- `io.netty.channel.EventLoop`
1. transport-native-epoll
	- `io.netty.channel.epoll`
	- `io.netty.channel.unix`
1. transport-rxtx
	- `io.netty.channel.rxtx`
1. transport-sctp
	- `io.netty.channel.sctp`
	- `com.sun.nio.sctp`
	- `io.netty.handler.codec.sctp`
1. transport-udt
	- `io.netty.channel.udt`
1. handler
	- `io.netty.handler.ipfilter`
	- `io.netty.handler.logging`
	- `io.netty.handler.ssl`
	- `io.netty.handler.stream`
	- `io.netty.handler.timeout`
	- `io.netty.handler.traffic`
1. handler-proxy
	- `io.netty.handler.proxy`
1. codec
    - codec: `io.netty.handler.codec`
    - dns: `io.netty.handler.codec.dns`
    - haproxy: `io.netty.handler.codec.haproxy`
    - http: `io.netty.handler.codec.http`
    - http2: `io.netty.handler.codec.http2`
    - memcache: `io.netty.handler.codec.memcache`
    - mqtt: `io.netty.handler.codec.mqtt`
    - socks: `io.netty.handler.codec.socksx`
    - xml: `io.netty.handler.codec.xml`

## 学习重点和进度

1. resolver
	- `io.netty.resolver`
1. buffer
	- `io.netty.buffer`(Ongoing)
1. transport
	- `io.netty.bootstrap`(Done)
	- `io.netty.channel`(Done)
	- `io.netty.channel.EventLoop`(Done)
1. handler
1. codec
    - codec: `io.netty.handler.codec`
    - http: `io.netty.handler.codec.http`
    - http2: `io.netty.handler.codec.http2`
