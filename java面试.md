## java面试

## 线程池是什么意思，线程有哪一些，请用java实现一个线程池。

线程池是指在初始化一个多线程应用程序过程中创建一个线程集合，然后再需要执行新的任务时重用这些线程而不是新建一个线程。线程池中线程的数量通常完全取决于可用内存数量和应用程序的需求。然而，增加可用线程数量是可能的。线程池中的每个线程都有被分配一个任务，一旦任务已经完成了，线程回到线程池中等待下一次分配任务。

一个线程池包括四个基本组成部分：

1.线程管理器：用于创建并管理线程池，包括创建线程池，销毁线程池，添加新任务；

2.工作线程：线程池中线程，在没有任务的时候处于等待状态，可以循环的执行任务；

3.任务接口：每个任务必须实现的接口，以供工作线程调度任务的执行，它主要规定了任务的入口，任务执行完后的收尾工作，任务的执行状态等；

4.任务队列：用于存放没有处理的任务，提供一种缓存机制。

## java Thread中run和start的区别

1.start方法

用start 方法来启动线程，是真正实现了多线程。通过调用Thread类的start方法来启动一个线程，这个线程处于就绪状态，并没有运行，一旦得到cpu时间片，就开始执行run方法。但要注意的是，此时不需要等待run方法执行完毕，可以继续执行下面的代码，所以run方法没有实现多线程。

2.run方法

run方法只是类的一个普通方法而已，如果直接调用Run方法，程序中依然只有主线程这一个线程，其程序执行路径还是只有一条，还是要顺序执行，只有等run方法执行完毕后才可以执行下面的代码。

## 涉及到静态初始化代码的继承

1）执行父类静态代码块

2）执行子类的静态代码块

3）执行父类的构造代码块

4）执行父类的构造函数

5）执行子类的构造代码块

6）执行子类的构造函数

## for循环执行顺序

for(条件1;条件2;条件3) ｛

  //语句

}

执行顺序：条件1＝》条件2=》语句＝》条件3=》条件2=》语句＝》条件3.。。

## Object有哪些方法

public方法：getClass, equals, hashCode, toString, t, notify

protected方法：clone, finalize

private方法：registerNatives

## 单例模式

单例模式保证只有一个实力存在。有时候单例是为了避免重复创建多个单例造成资源浪费，有时候也是为了避免多个不同的单例导致系统不一致的行为。

```
Class Singleton {
  private volatile static Singleton instance;
  
  private Singleton() {}
  
  public static Singleton getInstance() {
    if (instance == null) {
      synchronized (Singleton.class) {
        if (instance == null) {
          instance = new Singleton();
        }
      }
    }
    return instance;
  }
}
```

## HashMap和HashTable的区别

* HashMap允许键和值是null，HashTable则不允许
* HashTable是同步的，而HashMap则不是，因此，HashMap更适合单线程环境

