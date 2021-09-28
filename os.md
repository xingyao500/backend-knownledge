

### 进程直接操作物理内存问题？

1. 进程间访问的内存地址会重叠，当 A 进程访问的内存地址被 B 进程使用时，必须先把内存的数据拷贝到磁盘，然后将 A 进程的数据装载到内存，导致进程内存读写效率低下。
2. 进程间访问的内存地址不受权限控制，每个进程可以访问任意内存，存在安全风险。
3. 因为物理内存是唯一的，进程可访问的内存地址不一定连续，可能是离散的，导致操作内存比较困难。

### 虚拟内存

当一个进程创建时，操作系统会分配给它一段连续的虚拟内存地址。当执行时由操作系统将虚拟内存地址映射为相应的物理内存地址。

### 内存模型

地址从高到低：

| 分区   | 说明                                                 |
| ------ | ---------------------------------------------------- |
| stack  | 函数参数、局部变量，编译器自动分配内存，地址向低发展 |
| heap   | 运行期间动态分配内存，地址向高发展                   |
| static | 全局或静态变量                                       |
| Text   | 代码片段                                             |

### 进程

进程是指计算机中已运行的程序，当一段程序加载进内存中时它就变成了进程，通常进程的内存模型可以分为 4 块：栈区、堆区、文本区、数据区。

**进程控制块（PCB）** 代表进程的状态：
- 进程状态
- 进程 id
- 进程调度信息：优先级
- 程序计数器（下一个指令地址）
- 寄存器
- 文件状态
- 设备状态

### 线程

os 调度最小单位，被包含在进程之中，是一段单一顺序控制流。线程间共享进程资源同时又拥有自身的栈区。