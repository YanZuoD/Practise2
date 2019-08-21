# Practise2
## 1.Why should you have minimum scope for variables?
#### 可以增强代码的可读性和可维护性，并降低出错的可能性
## 2.Why should you understand performance of String Concatenation?
#### 字符串连接主要有四种方式：+,.concat,StringBulider.append,StringBuffer.append
#### 1.+连接：
####  由于底层的实现连接时，每+一次都会新增一个StringBuilder来进行增加，同事生成一个String对象，对于大量字符串连接来说，创建的这些StringBuilder和String是非常浪费性能的，所以+连接只适合少量字符串连接
#### 2.concat
####  cancat底层实现采用的char类型的buf数组扩容来进行连接，且由于concat扩容方式是倍数级扩容，虽然每次连接也会生成一个String对象，相比于+连接，效率会好很多。
#### 3.StringBuffer.append()
####  StringBuffer底层实现调用的父类AbstractStringBuilder的append方法，并重写toString方法做到了“保护性拷贝”，同时扩容方式是指数型方式。所以对于大量的字符串连接来说，StringBuffer的连接效率比.concat高很多，但是对于少量字符串连接，由于Stringbuufer采用的是调用栈更深的保护性拷贝，所以会比.concat要慢一些
#### 4.Stringbuilder.append()
####  StringBuilder.append()同StringBuffer类似，但是它相比StringBuffer相比，少了sychronized来保证线程安全，所以性能会比StringBuffer更快一些。
## 3.What are the best practices with Exception Handling?
#### 异常的最佳实践主要有：
#### 1.永远不要吞下异常
#### 2.不要捕获Throeable类
#### 3.要么记录异常要么抛出异常，不要一起执行
#### 4.finally中不要抛出异常
#### 5.始终只捕获实际可处理的异常
#### 6.不使用printStackTrace()语句或类似的方法
#### 7.早throw晚catch
#### 8.清理总是在处理异常之后
#### 9.不使用异常来控制流程
#### 10.不要catch最高层次的exception
#### 11.尽量减小try的代码块
#### 12.及时释放资源
## 4. When is it recommended to prefer Unchecked Exceptions?
#### 对于程序逻辑本身有问题，但是可以避免的异常推荐使用。对于这种异常，编译器不会强制你检查这种异常，而是根据业务的实际情况来判定是否需要使用未检查的异常来作为业务访问逻辑
## 5.When do you use a Marker Interface?
#### Marker Interface 主要用于弥补编程语言本身不支持为类维护元数据的问题，常用的Marker Interface有Serializable、Cloneable,这类主要是要是作为实现他们的子类的元数据来用的，在JDK1.5以后，注解的方式可以为类补充元数据，而在jdk1.5则主要使用Marker Interface。
## 6.Why are ENUMS important for Readable Code? 
#### 1.让代码可读性更高
#### 2.增加代码维护性
## 7.What is functional progtamming?
#### 函数式编程是一种抽象程度很高的编程范式，纯粹的函数式编程语言编写的函数没有变量，因此，任意一个函数，只要输入是确定的，输出就是确定的，这种纯函数我们称之为没有副作用。而允许使用变量的程序设计语言，由于函数内部的变量状态不确定，同样的输入，可能得到不同的输出，因此，这种函数是有副作用的。函数式编程的一个特点就是，允许把函数本身作为参数传入另一个函数，还允许返回一个函数。
## 8.Why should you prefer Builder Pattern to build complex objects?
#### 更加接近要抽取的对象的含义，能更好的封装内部结构，对使用者来说放心的去构造就好，不用担心顺序之类的问题。通过使用方式来看，可以传递各种类型的值，然后使用这种链式的调用，使代码看起来非常简洁调用也很方便。
## 9.Why should you avoid floats for Calculations?
#### 浮点的编码跟整数编码是不一样的，计算时需要专门的寄存器和浮点计算单元来处理，一个浮点运算指令使用的CPU周期也更长，因此对于内核来说就会想尽量回避浮点数运算，譬如说浮点数经过定点整数转换后进行运算，效率会高很多，即使CPU带有浮点数运算部件，一般内核还是要避免直接进行浮点数运算，因为这些部件有可能被用户进程占用了，内核要判断这些浮点数部件是否被占用，保护现场，然后用浮点运算部件计算结果，恢复现场，开销会很大。
## 10.Why should you build the riskiest high priority features first?
#### 高风险的模块往往需要经过很长的时间来验证和完善，优先构建能保证充足的时间去验证。
