### java 类加载机制

- 加载
  - 加载只是类加载的一个环节
- 连接
  - 包括验证，准备，解析等活动
  - 解析部分是灵活的，可以在初始化之后进行，实现后期绑定，其他环节是固定的。
- 初始化

### 双亲委派模型

- Bootstrap -》 Exception -》Application -》UserClassLoader
  每个类加载器加载的类都拥有单独的命名空间
  假设用户类加载器加载了A类，别的类加载器也加载了A类，用instanceof去比较，返回的时false
- 如果出现了多个A类，会造成混乱，jvm如何实现只加载一个A类呢？毕竟instanceof比较时不同加载器加载的同一个类结果是false，这时候就引入了双亲委派模型，
- 在双亲委派模型中，儿子加载器会调用父亲加载器，如果父亲加载器无法完成加载，则儿子加载器进行加载，这种调用的传递会一致向父亲，，父亲的父亲传递。
  什么是无法加载呢？就是加载器无法在自己负责的加载路径中找到该类。
- 双亲委派模型不是银弹，