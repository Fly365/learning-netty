# 类HttpServerCodec

类HttpServerCodec是HttpRequestDecoder和HttpResponseEncoder的组合，可以简化HTTP的服务器端实现。

## 类定义

```java
public final class HttpServerCodec extends CombinedChannelDuplexHandler<HttpRequestDecoder, HttpResponseEncoder>
        implements HttpServerUpgradeHandler.SourceCodec {
}
```




