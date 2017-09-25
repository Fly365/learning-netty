# http类实现

## 基础实现类

![](images/basic-http-classes.png)

### 类DefaultHttpObject

提供了类成员decoderResult，仅此而已。

```java
public class DefaultHttpObject implements HttpObject {
	private DecoderResult decoderResult = DecoderResult.SUCCESS;
}
```

### 类DefaultHttpMessage

提供了类成员version和headers，。

```java
public abstract class DefaultHttpMessage extends DefaultHttpObject implements HttpMessage {
    private HttpVersion version;
    private final HttpHeaders headers;
}
```

有两个细节，后面再看：

1. headers是final，但是version不是，而是有一个setProtocolVersion(HttpVersion version)方法可以用来设置
2. DefaultHttpMessage是抽象类，但是它继承的DefaultHttpObject却不是抽象类

```java
protected DefaultHttpMessage(final HttpVersion version, boolean validateHeaders, boolean singleFieldHeaders) {
    this.version = checkNotNull(version, "version");
    headers = singleFieldHeaders ?
    	new CombinedHttpHeaders(validateHeaders):
        new DefaultHttpHeaders(validateHeaders);
}
```

### 类DefaultHttpContent
### 类DefaultLastHttpContent
### 类DefaultHttpRequest
### 类DefaultHttpResponse

## 全数据实现类

![](images/full-http-classes.png)

### 类DefaultFullHttpResponse

### 类DefaultFullHttpRequest

