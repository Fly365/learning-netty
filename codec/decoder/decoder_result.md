# Decoder Result

## DecoderResult

解码的结果只有三种： unfinished，success，failure。

为`UNFINISHED`和`SUCCESS`定义了两个`Signal`常量和DecoderResult常量：

```java
protected static final Signal SIGNAL_UNFINISHED = Signal.valueOf(DecoderResult.class, "UNFINISHED");
protected static final Signal SIGNAL_SUCCESS = Signal.valueOf(DecoderResult.class, "SUCCESS");

public static final DecoderResult UNFINISHED = new DecoderResult(SIGNAL_UNFINISHED);
public static final DecoderResult SUCCESS = new DecoderResult(SIGNAL_SUCCESS);
```

如果失败则记录失败原因，这个类只有一个类成员变量`cause`，所有的方法都是围绕它，如构造方法：

```java
private final Throwable cause;
protected DecoderResult(Throwable cause) {
    if (cause == null) {
        throw new NullPointerException("cause");
    }
    this.cause = cause;
}
```

定义了几个判断方法来获取解码的结果：

```java
public boolean isFinished() {
    return cause != SIGNAL_UNFINISHED;
}

public boolean isSuccess() {
    return cause == SIGNAL_SUCCESS;
}

public boolean isFailure() {
    return cause != SIGNAL_SUCCESS && cause != SIGNAL_UNFINISHED;
}
```

## DecoderResultProvider

为被解码的消息的`DecoderResult`属性提供访问方法。

```java
public interface DecoderResultProvider {
    /**
     * 返回解码这个对象的结果
     */
    DecoderResult decoderResult();

    /**
     * 更新解码这个对象的结果。
     * 这个方法应该由解码器调用。
     * 不要调用这个方法，除非你知道自己在做什么。
     */
    void setDecoderResult(DecoderResult result);
}
```




