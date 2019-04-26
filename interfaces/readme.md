# 概览

本目录讲解和Collection相关的接口

## 1 Cloneable

<pre>
实现了Cloneable接口的类可以使用Object的clone方法，也就是说具备clone的能力
在未实现clone接口的类上调用clone方法，会抛出CloneNotSupportedException的异常
按照惯例，实现了此接口的类应该重写clone方法以达到clone的能力
请注意，此接口不包含克隆方法。 因此，仅仅通过实现该接口的事实来克隆对象是不可能的。 即使反射调用clone方法，也无法保证它会成功。
</pre>

## 2 Serializable

<pre>
实现java.io.Serializable接口的类启用了类的可序列化。 未实现此接口的类将不会将其任何状态序列化或反序列化。 可序列化类的所有子类型本身都是可序列化的。 序列化接口没有方法或字段，仅用于标识可序列化的语义。
序列化保存的是对象的状态，静态变量属于类的状态，因此 序列化并不保存静态变量。
transient关键字用于限定对应的属性不被序列化和反序列化
当一个父类实现序列化，子类自动实现序列化，不需要显式实现Serializable接口。
一个子类实现了 Serializable 接口，它的父类都没有实现 Serializable 接口，要想将父类对象也序列化，就需要让父类也实现Serializable 接口。
</pre>

## 3 RandomAccess

<pre>
实现了此接口的类，表示它们支持快速（通常是恒定时间）随机访问。此接口的主要目的是允许通用算法更改其行为，以便在应用于随机或顺序访问列表时提供良好的性能。
随机访问可以在很大程度上提升性能，比如ArrayList，但是有些类型性能就偏差，比如LinkedList。Collections都具备这样的能力
</pre>

## 4 Runnable

<pre>
Runnable接口应该由任何其实例要由线程执行的类实现。该类必须定义一个无参的run方法。
此接口旨在为希望在活动时执行代码的对象提供通用协议。例如，Runnable由Thread类实现。活动只是意味着一个线程已经启动但尚未停止。
在线程中运行时，需要将实现类实例本身作为参数传递给Thread，只需要重写run()方法。
如果不打算修改或增强类的基本行为，那么推介使用实现接口而非继承类的方案
</pre>

### 4.1 方法介绍

* run()方法

当使用实现接口Runnable的对象来创建线程时，启动该线程会导致在该单独执行的线程中调用对象的run方法。

## Callable

<pre>
返回结果并可能抛出异常的任务。实现者定义一个没有名为{@code call}的参数的方法。
{@code Callable}接口类似于{@link java.lang.Runnable}，因为它们都是为其实例可能由另一个线程执行的类而设计的。 但是，{@ code Runnable}不返回结果，也不能抛出已检查的异常。
{@link Executors}类包含将其他常用表单转换为{@code Callable}类的实用程序方法。
</pre>