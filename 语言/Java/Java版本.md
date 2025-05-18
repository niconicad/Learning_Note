# JAVA



## Java各个版本特性

Java的不同版本在性能、安全性、语言特性、API等方面做了逐步的改进和扩展。以下是各个主要版本的详细特性概述：

### **Java 1.0 (1996)**
- **基本特性**：
  - Java的第一个版本，推出了基本的Java语言和核心库。
  - 具备了面向对象编程（OOP）特性、垃圾回收（GC）、跨平台的Java虚拟机（JVM）等功能。
  
### **Java 1.1 (1997)**
- **增强的特性**：
  - 引入了**内存垃圾回收**机制，减少了内存泄漏问题。
  - 引入了**JDBC**（Java数据库连接）来简化数据库操作。
  - 增加了**RMI**（远程方法调用）支持，允许在不同的计算机之间执行方法调用。
  - 增强的事件监听机制，增加了Swing GUI库。

### **Java 1.2 (1998)**
- **重要更新**：
  - **Swing**图形用户界面（GUI）库替代了原有的AWT。
  - 引入了**集合框架**（Collection Framework），提供了更丰富的数据结构（如List、Set、Map）。
  - 引入了**JIT编译器**（即时编译器），提高了性能。
  - 引入了**Java Plug-in**和**Java IDL**（接口定义语言）。
  
### **Java 1.3 (2000)**
- **性能提升与增强**：
  - 引入了**JavaSound**，支持更丰富的音频功能。
  - 引入了**J2EE**（Java 2平台企业版）用于开发企业级应用。
  - 性能增强，JVM改进了垃圾回收机制。

### **Java 1.4 (2002)**
- **重要新特性**：
  - 引入了**正则表达式**（java.util.regex）。
  - 引入了**NIO（New I/O）**，使得Java对输入输出（I/O）操作更加高效。
  - 增强了**JVM的可调性**，提供了更多调试和日志工具。
  - 引入了**断言**（assert）功能。
  
### **Java 5 (Java 1.5) (2004)**
- **重大更新**：
  - 引入了**泛型**（Generics），提供了更强的类型安全。
  - 引入了**枚举**（Enums）类型，简化了常量的管理。
  - 引入了**增强型for循环**（for-each），简化了集合的遍历。
  - 引入了**注解**（Annotations），允许程序动态添加元数据。
  - 引入了**并发包**（java.util.concurrent），支持多线程编程。
  - 引入了**自动拆装箱**（autoboxing），简化了基本类型和包装类型之间的转换。

### **Java 6 (2006)**
- **性能提升与优化**：
  - 引入了**Java Compiler API**，使得开发者能够在应用中编译Java源代码。
  - 引入了**脚本引擎**（JSR 223），允许在Java程序中嵌入脚本语言，如JavaScript。
  - 提升了JVM性能和启动时间。
  - 引入了**Web服务支持**（JAX-WS和JAX-RS）以及**JMX（Java Management Extensions）**的改进。

### **Java 7 (2011)**
- **新特性**：
  - 引入了**try-with-resources**语句，简化了资源管理。
  - 引入了**二进制字面量**和**下划线分隔数字**（支持数字字面量中添加下划线来提高可读性）。
  - 改进了**NIO 2.0**，为文件系统提供了更强大的操作API。
  - 引入了**Fork/Join框架**，支持分治算法，优化并行任务处理。
  - 提高了JVM性能和垃圾回收机制。
  
### **Java 8 (2014)**
- **革命性变化**：
  - 引入了**Lambda表达式**，使得函数式编程风格成为Java的一部分。
  - 引入了**Stream API**，使得处理集合数据变得更加简洁。
  - 引入了**java.time包**，提供了现代的日期和时间API。
  - **默认方法**（Default Methods）允许接口有方法实现，增强接口功能。
  - **Optional类**，减少NullPointerException的风险。
  - 强化了JVM性能和垃圾回收机制。

### **Java 9 (2017)**
- **模块化系统**：
  - 引入了**Java Platform Module System (JPMS)**，将JDK划分为多个模块，提高了JDK的可维护性、可扩展性。
  - 引入了**JShell**，一个交互式的命令行工具，支持REPL（Read-Eval-Print Loop）编程。
  - 提升了JVM性能，增强了JVM的诊断和调试工具。
  
### **Java 10 (2018)**
- **局部变量类型推断**：
  - 引入了**`var`关键字**，允许开发者省略局部变量的类型，自动推断类型。
  - 提升了垃圾回收（G1垃圾回收器）。
  - 引入了**JVM改进**，提高了性能和可扩展性。
  
### **Java 11 (2018)**
- **LTS版本（长期支持）**：
  - 引入了新的API和性能优化。
  - **HttpClient** API标准化，提供了更易用的HTTP客户端API。
  - 删除了许多过时的和不再维护的模块，如Java EE和CORBA。
  - 引入了**Lambda参数类型推断**，简化了Lambda表达式的参数类型。
  - 提升了垃圾回收和JVM性能。

### **Java 12 (2019)**
- **性能提升与垃圾回收**：
  - 引入了**Shenandoah垃圾回收器**，提供低延迟的垃圾回收。
  - 引入了**JVM常量API**，提高了JVM运行时常量的访问效率。
  - 改进了**ZGC（Z Garbage Collector）**，提高了低延迟性能。

### **Java 13 (2019)**
- **增强功能**：
  - **文本块**（Text Blocks）引入，简化多行字符串的处理。
  - 引入**动态CDS类数据共享**，优化JVM启动性能。
  
### **Java 14 (2020)**
- **新特性**：
  - 引入了**NVM（Non-Volatile Memory）**的实验性支持。
  - 引入了**JEP 358**，支持**增强的Foreign Function API**，使得Java能够更高效地调用本地代码。
  
### **Java 15 (2020)**
- **新特性**：
  - 引入了**ZGC（Z Garbage Collector）**的进一步优化。
  - 引入**Hidden Classes**，允许加载不被访问的类。

### **Java 16 (2021)**
- **增强和功能**：
  - 引入了**JEP 376**，添加了对密封类的支持，允许限制继承类。
  - 引入了**JEP 391**，为Linux系统添加了对OpenJDK的原生映像支持。

### **Java 17 (2021)**
- **LTS版本**：
  - 引入了密封类（Sealed Classes），提供更多对继承关系的控制。
  - 强化了JVM性能，提升了G1垃圾回收。

### **Java 18 (2022)**
- **新特性**：
  - 引入了对**JEP 400**的支持，使得JVM支持对UTF-8编码的全面支持。
  - 改进了**JEP 421**，增强了Java的性能调优工具。

### **Java 19 (2022)**
- **更多优化和改进**：
  - 引入**JEP 409**，支持密封类（Sealed Classes）的多重扩展。

### **Java 20 (2023)**
- **新特性**：
  - 引入了更先进的**垃圾回收器**优化。
  - 引入**JEP 419**，使得Java的运行时支持更复杂的操作。

Java的每个新版本都包含了对语言、性能、API以及JVM的优化和改进，使得开发人员能够利用更高效、简洁的工具来编写代码。



## Java容器

好的，以下是更为详细和完善的 Java 常用容器类及其特性，包括它们的主要实现、通用方法、以及每个容器类的显著特点。

### **1. Collection 接口**

`Collection` 是 Java 集合框架的根接口，它代表一个对象的集合，所有集合类（如 `List`, `Set`, `Queue`）都实现了该接口。

#### **通用特性：**
- **动态大小**：Java 集合类通常会自动扩展大小以适应元素的添加。
- **支持泛型**：集合类支持使用泛型来确保类型安全。
- **支持迭代**：集合类提供了 `iterator()` 方法，用于遍历集合中的元素。

#### **常见方法：**
- `add(E e)`: 向集合添加元素。
- `addAll(Collection<? extends E> c)`: 向集合中添加另一个集合的元素。
- `clear()`: 清空集合。
- `contains(Object o)`: 判断集合中是否包含指定元素。
- `isEmpty()`: 判断集合是否为空。
- `size()`: 获取集合的元素数量。
- `toArray()`: 将集合转换为数组。
- `remove(Object o)`: 从集合中删除指定元素。

---

### **2. List 接口**

`List` 是一个有序集合，它允许重复的元素，并且可以通过索引访问元素。

#### **常见实现类**：
- **ArrayList**:
  - **特点**：基于动态数组实现，支持快速随机访问。添加和删除元素会涉及数组的重新分配和元素移动，因此在执行大量插入和删除操作时性能较差。
  - **性能**：获取元素速度快，但插入/删除性能差（尤其是在数组中间插入/删除时）。

- **LinkedList**:
  - **特点**：基于双向链表实现，支持快速的插入和删除操作。
  - **性能**：适用于需要频繁插入和删除操作的场景，尤其是在中间插入时比 `ArrayList` 更高效。

- **Vector**:
  - **特点**：类似于 `ArrayList`，但是它是线程安全的，通常比 `ArrayList` 慢。
  - **性能**：线程安全，但性能较差。

#### **常见方法：**
- `add(int index, E element)`: 在指定位置插入元素。
- `get(int index)`: 获取指定位置的元素。
- `set(int index, E element)`: 替换指定位置的元素。
- `remove(int index)`: 删除指定位置的元素。
- `indexOf(Object o)`: 返回元素首次出现的索引。
- `size()`: 获取列表中元素的个数。
- `subList(int fromIndex, int toIndex)`: 返回指定区间的子列表。
  
---

### **3. Set 接口**

`Set` 是一个不允许重复元素的集合。与 `List` 不同，`Set` 的元素无序。

#### **常见实现类**：
- **HashSet**:
  - **特点**：基于哈希表实现，元素无序，查找和插入操作的时间复杂度为 O(1)。
  - **性能**：由于不维护元素的顺序，`HashSet` 在插入、删除、查找等操作上的性能较优。

- **LinkedHashSet**:
  - **特点**：继承自 `HashSet`，它维护了元素的插入顺序，元素按插入顺序存储。
  - **性能**：在保持元素插入顺序的同时，性能与 `HashSet` 相似。

- **TreeSet**:
  - **特点**：基于红黑树实现，元素是有序的，支持排序操作。
  - **性能**：插入和删除操作的时间复杂度是 O(log n)，适用于需要排序的场景。

#### **常见方法：**
- `add(E e)`: 向集合中添加元素。
- `remove(Object o)`: 删除集合中的指定元素。
- `contains(Object o)`: 检查集合中是否包含指定元素。
- `isEmpty()`: 检查集合是否为空。
- `size()`: 获取集合中元素的数量。
  
---

### **4. Queue 接口**

`Queue` 是一个用于存储待处理元素的集合，遵循先进先出（FIFO）原则。

#### **常见实现类**：
- **LinkedList**:
  - **特点**：不仅是 `List` 的实现，还实现了 `Queue` 接口，适用于双端队列操作（即可以在两端插入和删除元素）。
  
- **PriorityQueue**:
  - **特点**：实现了优先队列，元素按照自然顺序或自定义顺序排序。
  - **性能**：插入操作的时间复杂度是 O(log n)，适用于优先级处理。

#### **常见方法：**
- `offer(E e)`: 添加元素（如果队列已满，则返回 `false`）。
- `poll()`: 获取并移除队列头部元素，若队列为空，返回 `null`。
- `peek()`: 获取队列头部元素，但不移除它。
- `size()`: 获取队列中的元素数量。
  
---

### **5. Map 接口**

`Map` 是一个用于存储键值对的集合，它不允许键重复，但值可以重复。

#### **常见实现类**：
- **HashMap**:
  - **特点**：基于哈希表实现，元素无序，支持通过键快速查找值。
  - **性能**：插入、删除和查找操作的时间复杂度为 O(1)。

- **LinkedHashMap**:
  - **特点**：继承自 `HashMap`，保持元素的插入顺序，常用于需要按照插入顺序遍历键值对的场景。
  - **性能**：由于额外的链表维护，它的插入和查找性能稍低于 `HashMap`。

- **TreeMap**:
  - **特点**：基于红黑树实现，键值对按键排序。
  - **性能**：插入和删除操作的时间复杂度为 O(log n)，适用于需要按顺序存储键值对的场景。

#### **常见方法：**
- `put(K key, V value)`: 向 Map 中添加键值对。
- `get(Object key)`: 根据键获取值。
- `containsKey(Object key)`: 检查是否包含指定的键。
- `remove(Object key)`: 删除指定键的键值对。
- `keySet()`: 返回 Map 中所有的键。
- `values()`: 返回 Map 中所有的值。
- `entrySet()`: 返回 Map 中的键值对集合。

---

### **6. Concurrent Collections (并发集合类)**

Java 提供了线程安全的集合类，特别适合于多线程环境中使用。

#### **常见实现类**：
- **CopyOnWriteArrayList**:
  - **特点**：线程安全，适用于读多写少的场景。每次写操作都会复制数组，因此适合并发读操作多于写操作的场景。

- **ConcurrentHashMap**:
  - **特点**：高效的线程安全哈希表，采用分段锁机制来提高并发性能。
  - **性能**：支持高并发的线程安全操作，比 `Hashtable` 性能更优。

#### **常见方法**：
- 与普通集合方法相似，但这些类实现了线程安全的操作，如 `putIfAbsent()`，`remove()`，`replace()` 等。

---

### **7. Stack 和 Deque**

- **Stack**:
  - **特点**：继承自 `Vector`，实现了 LIFO（后进先出）结构。`Stack` 是线程安全的，但由于其性能问题，通常不推荐使用。
  - **常用方法**：
    - `push(E item)`：压栈操作。
    - `pop()`：弹栈操作。
    - `peek()`：获取栈顶元素但不移除。

- **Deque**（双端队列）:
  - **特点**：支持从两端插入和删除元素，通常用于实现队列和栈。
  - **常用实现类**：`ArrayDeque`、`LinkedList`。
  - **常用方法**：
    - `addFirst(E e)`：从头部添加元素。
    - `addLast(E e)`：从尾部添加元素。
    - `removeFirst()`：移除头部元素。
    - `removeLast()`：移除尾部元素。
    - `peekFirst()`：查看头部元素但不移除。



## 继承关系

~~~
Collection (接口)
├── List (接口)
│   ├── ArrayList
│   ├── LinkedList
│   ├── Vector
│   ├── Stack
│   ├── CopyOnWriteArrayList
├── Set (接口)
│   ├── HashSet
│   ├── LinkedHashSet
│   ├── TreeSet
│   ├── CopyOnWriteArraySet
├── Queue (接口)
│   ├── LinkedList
│   ├── PriorityQueue
│   ├── ArrayDeque
│   ├── ConcurrentLinkedQueue
│   ├── LinkedBlockingQueue
│   ├── ArrayBlockingQueue
│   └── PriorityBlockingQueue
└── Deque (接口)
    ├── LinkedList
    ├── ArrayDeque
    └── ConcurrentLinkedDeque

Map (接口)
├── HashMap
├── LinkedHashMap
├── TreeMap
├── Hashtable
├── WeakHashMap
├── IdentityHashMap
├── ConcurrentHashMap
└── Properties

~~~

以下是 Java 主要版本的详细总结，包括 **重要特性** 和 **使用案例**，以表格形式呈现：

------

### **Java 重要版本及特性总结**

| **版本**     | **代号/年份**     | **核心特性**                                                 | **使用案例**                                                 |
| ------------ | ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Java 1.0** | Oak (1996)        | - 初版 Java 语言 - 基础类库（`java.lang`, `java.util`） - Applet 支持 | 简单的 GUI 程序（如早期网页动画）                            |
| **Java 1.2** | Playground (1998) | - 集合框架（`List`, `Map`） - JIT 编译器 - `strictfp` 关键字 - Swing GUI 库 | 企业级应用（如银行系统）                                     |
| **Java 5**   | Tiger (2004)      | - 泛型（Generics） - 注解（`@Override`） - 自动装箱/拆箱 - 枚举（`enum`） - 可变参数（`varargs`） | 简化集合操作（如 `List<String>`）、框架开发（Spring 注解驱动） |
| **Java 7**   | Dolphin (2011)    | - `try-with-resources` - 钻石操作符（`<>`） - NIO.2（`Files`, `Paths`） - `String` switch 支持 | 文件操作（如递归删除）、资源自动管理（JDBC 连接）            |
| **Java 8**   | Spider (2014)     | - Lambda 表达式 - Stream API - `Optional` - 新的日期时间 API（`java.time`） - 默认方法（`default`） | 函数式编程（如集合过滤 `list.stream().filter(...)`）、日期处理（`LocalDate`） |
| **Java 11**  | LTS (2018)        | - HTTP Client（标准库） - `var` 局部变量推断 - `String` 新增方法（`isBlank()`, `lines()`） - 移除 Java EE 模块 | REST 调用（`HttpClient`）、简化代码（`var list = new ArrayList<>()`） |
| **Java 17**  | LTS (2021)        | - 密封类（`sealed class`） - `switch` 表达式增强 - 文本块（`"""`） - 新的垃圾收集器（ZGC/Shenandoah） | 安全建模（限制继承）、JSON 字符串处理（多行文本）            |
| **Java 21**  | LTS (2023)        | - 虚拟线程（Virtual Threads） - `switch` 模式匹配 - 记录模式（Record Patterns） - 结构化并发 | 高并发应用（百万级线程）、模式匹配（`case Point(int x, int y)`） |

------

### **关键特性详解与案例**

#### **1. Java 5 - 泛型（Generics）**

java

复制

```java
// 泛型集合
List<String> names = new ArrayList<>();  // 编译时类型检查
names.add("Alice"); 
// names.add(123); // 编译错误
```

#### **2. Java 8 - Lambda 与 Stream**

java

复制

```java
// 过滤并计算平均值
List<Integer> numbers = Arrays.asList(1, 2, 3, 4);
double avg = numbers.stream()
                   .filter(n -> n % 2 == 0)
                   .mapToInt(n -> n)
                   .average()
                   .orElse(0);
```

#### **3. Java 11 - HTTP Client**

java

复制

```java
HttpClient client = HttpClient.newHttpClient();
HttpRequest request = HttpRequest.newBuilder()
        .uri(URI.create("https://api.example.com/users"))
        .build();
client.sendAsync(request, HttpResponse.BodyHandlers.ofString())
      .thenApply(HttpResponse::body)
      .thenAccept(System.out::println);
```

#### **4. Java 17 - 密封类（Sealed Classes）**

java

复制

```java
public sealed interface Shape permits Circle, Rectangle { }
public final class Circle implements Shape { /*...*/ }
public final class Rectangle implements Shape { /*...*/ }
// 编译时限制子类
```

#### **5. Java 21 - 虚拟线程（Virtual Threads）**

java

复制

```java
try (var executor = Executors.newVirtualThreadPerTaskExecutor()) {
    IntStream.range(0, 10_000).forEach(i -> 
        executor.submit(() -> {
            Thread.sleep(Duration.ofSeconds(1));
            return i;
        })
    );
} // 自动关闭线程池
```

------

### **版本选择建议**

| **场景**               | **推荐版本** | **原因**                                       |
| ---------------------- | ------------ | ---------------------------------------------- |
| 企业长期支持（LTS）    | Java 17/21   | 长期维护、稳定性高（Oracle 提供至少 8 年支持） |
| 微服务/云原生          | Java 21      | 虚拟线程提升并发性能（支持百万级连接）         |
| Android 开发（兼容性） | Java 8/11    | 部分特性受 Android SDK 限制                    |
| 学习/个人项目          | Java 21      | 体验最新语法（如记录类、模式匹配）             |

------

### **总结**

- **Java 8** 是分水岭（Lambda/Stream），至今广泛使用。
- **Java 11** 和 **Java 17** 是 LTS 版本，适合生产环境。
- **Java 21** 引入虚拟线程，适合高并发场景。

通过版本特性，可以写出更简洁、高效且安全的代码！ 🚀

