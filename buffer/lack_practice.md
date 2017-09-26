## 资源泄漏检测实战


启动时的日志打印，看到leakDetection.level设置为paranoid：

```bash
[main] [DEBUG] [io.netty.util.ResourceLeakDetector] - -Dio.netty.leakDetection.level: paranoid
[main] [DEBUG] [io.netty.util.ResourceLeakDetector] - -Dio.netty.leakDetection.maxRecords: 4
```

检测到泄漏时的日志：

```bash
[Mesh-Worker-3-49] [ERROR] [io.netty.util.ResourceLeakDetector] - LEAK: ByteBuf.release() was not called before it's garbage-collected. See http://netty.io/wiki/reference-counted-objects.html for more information.
Recent access records: 1
#1:
	Hint: 'MeshHttpServerHandler#0' will handle the message from this point.	io.netty.buffer.AdvancedLeakAwareCompositeByteBuf.touch(AdvancedLeakAwareCompositeByteBuf.java:1040)
......	io.netty.util.concurrent.DefaultThreadFactory$DefaultRunnableDecorator.run(DefaultThreadFactory.java:138)
	java.lang.Thread.run(Thread.java:748)
Created at:
	io.netty.util.ResourceLeakDetector.track(ResourceLeakDetector.java:237)
......	io.netty.util.concurrent.DefaultThreadFactory$DefaultRunnableDecorator.run(DefaultThreadFactory.java:138)
	java.lang.Thread.run(Thread.java:748)
```
