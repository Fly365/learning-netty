# Channel Factory

由于历史原因，现在netty内有两个ChannelFactory类：

1. io.netty.bootstrap.ChannelFactory
2. io.netty.channe.ChannelFactory

## bootstrap.ChannelFactory

这个类在package `io.netty.bootstrap`中, 明显这个packge名不适合, 所以这个`io.netty.bootstrap.ChannelFactory`已经被标记为"@Deprecated".

```java
package io.netty.bootstrap;

@Deprecated
public interface ChannelFactory<T extends Channel> {
/**
 * Creates a new channel.
 */
T newChannel();
}
```

## channel.ChannelFactory

现在要求使用packge `io.netty.channel.ChannelFactory` 类, 这个新类的定义有点奇怪, 是从旧的bootstrap.ChannelFactory下继承:

```java
package io.netty.channel;

public interface ChannelFactory<T extends Channel> extends io.netty.bootstrap.ChannelFactory<T> {
    /**
     * Creates a new channel.
     */
    @Override
    T newChannel();
}
```

## ReflectiveChannelFactory

这是一个帮助创建Channel的工具类，给定要创建的Channel的类型，通过反射方式实现Channel的创建。

```java
package io.netty.channel;

public class ReflectiveChannelFactory<T extends Channel> implements ChannelFactory<T> {
	// 内部保存一个Class
    private final Class<? extends T> clazz;

	// 构造函数传入
    public ReflectiveChannelFactory(Class<? extends T> clazz) {
        if (clazz == null) {
            throw new NullPointerException("clazz");
        }
        this.clazz = clazz;
    }

    @Override
    public T newChannel() {
        try {
        	// 简单通过Class的newInstance()方法创建实例
            // 这也要求传入的Channel Class必须有默认构造函数
            return clazz.newInstance();
        } catch (Throwable t) {
            throw new ChannelException("Unable to create Channel from class " + clazz, t);
        }
    }
    ......
}
```

使用中这个类反而是最常用的，典型使用例子如下:

```java
ServerBootstrap b = new ServerBootstrap();
b.channel(NioServerSocketChannel.class);
```