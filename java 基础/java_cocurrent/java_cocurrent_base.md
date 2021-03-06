## java 并发基础
#### 线程

1. 通用线程生命周--线程状态
    - 初始状态 编程语言层面，线程已经已经创建，此时操作系统还没有创建线程，不允许分配cpu。
    - 可运行状态 操作系统已创建线程，可分配cpu状态
    - 运行状态 cpu空闲时，操作系统会分配cpu给一个可执行状态的线程，
    被分配cpu执行的线程为运行状态
    - 休眠状态 调用一个阻塞api(读文件)或者等待条件变量，让出cpu使用权，休眠状态的线程永远不能获得cpu的使用权除非转换为可执行状态。
    - 终止状态 程序正常结束，未捕获异常出现，终止状态线程生命周期结束。

```dot{engine="dot"}
digraph g {
    //节点关系
    初始化状态->可执行状态
    可执行状态->运行状态[dir=both]
    运行状态->终止状态;
    运行状态->休眠状态->可执行状态;
    //节点属性
    初始化状态[shape=polygon];
    可执行状态[shape=polygon];
    运行状态[shape=polygon];
    终止状态[shape=polygon];
    休眠状态[shape=polygon];
}
```

1. java线程状态
    - NEW (新创建状态，new Thread(r) 此时就处于new状态，在执行前准备的状态？？此时操作系统还没有创建线程)
    - RUNMABLE (可运行状态) 新创建的线程调用start的就处于该状态，此时线程可能运行也可能没有运行，依赖于，操作系统有没有分配cpu给该线程。
    - block，wait和timewaiting (阻塞和等待状态) 都是暂时不活动，他们区别在于进入该不活动状态的方式不用，wait 等待通知，block等待资源(说的不够清楚需要修改 TODO )  获取锁，等待的计时版本。
    - terminated 终止状态 两种情况进入该状态 程序正常结束或出现未捕获异常。

2. 通用线程状态与java线程状态对应

```dot{engine="circo"}
digraph g {
    //节点关系
    初始化状态->运行状态
    运行状态->休眠状态[dir=both];
    运行状态->终止状态
    //节点属性
    初始化状态[shape=polygon,label="初始化状态\nNEW"];
    运行状态[shape=polygon,label="可执行状态\nRUNMABLE"];
    终止状态[shape=polygon,label="终止状态\nTERMINATED"];
    休眠状态[shape=polygon,label="休眠状态\nBLOCK\nWAIT\nTIMEWAITING"];
}
```