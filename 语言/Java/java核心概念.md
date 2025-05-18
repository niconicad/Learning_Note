# Java核心概念详解

Java作为一门广泛使用的编程语言，拥有一套完整的核心概念体系。下面我将从基础到高级，系统性地讲解Java的核心概念。

## 一、基础语法概念

### 1. 数据类型

**基本数据类型**：

- 整型：byte(1字节)、short(2)、int(4)、long(8)
- 浮点型：float(4)、double(8)
- 字符型：char(2)
- 布尔型：boolean(1)

**引用数据类型**：

- 类(class)
- 接口(interface)
- 数组(array)

### 2. 变量与常量

java

复制

```java
int age = 25; // 变量
final double PI = 3.14159; // 常量
```

### 3. 运算符

- 算术运算符：+ - * / % ++ --
- 关系运算符：== != > < >= <=
- 逻辑运算符：&& || !
- 位运算符：& | ^ ~ << >> >>>
- 赋值运算符：= += -= *= /= %= &= |= ^= <<= >>= >>>=
- 三目运算符：? :

## 二、面向对象编程(OOP)核心

### 1. 类与对象

java

复制

```java
public class Person {
    // 属性(字段)
    private String name;
    private int age;
    
    // 构造方法
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    // 方法
    public void introduce() {
        System.out.println("我叫" + name + "，今年" + age + "岁");
    }
}

// 创建对象
Person p = new Person("张三", 25);
p.introduce();
```

### 2. 四大特性

**封装**：

- 将数据和行为包装在类中
- 通过访问修饰符控制可见性(private/protected/public)

**继承**：

java

复制

```java
public class Student extends Person {
    private String school;
    
    public Student(String name, int age, String school) {
        super(name, age); // 调用父类构造方法
        this.school = school;
    }
    
    @Override
    public void introduce() {
        super.introduce();
        System.out.println("我在" + school + "上学");
    }
}
```

**多态**：

- 编译时多态(方法重载)
- 运行时多态(方法重写)

**抽象**：

- 抽象类(abstract class)
- 接口(interface)

### 3. 接口与抽象类

**接口**：

java

复制

```java
public interface Animal {
    void eat();
    void sleep();
}

public class Dog implements Animal {
    @Override
    public void eat() {
        System.out.println("狗在吃东西");
    }
    
    @Override
    public void sleep() {
        System.out.println("狗在睡觉");
    }
}
```

**抽象类**：

java

复制

```java
public abstract class Shape {
    public abstract double area(); // 抽象方法
    
    public void display() {
        System.out.println("面积是: " + area());
    }
}

public class Circle extends Shape {
    private double radius;
    
    public Circle(double r) {
        this.radius = r;
    }
    
    @Override
    public double area() {
        return Math.PI * radius * radius;
    }
}
```

## 三、异常处理

### 1. 异常体系

markdown

复制

```markdown
Throwable
    ├── Error (系统错误，通常不处理)
    └── Exception
        ├── RuntimeException (运行时异常)
        └── 其他检查型异常(Checked Exception)
```

### 2. 异常处理机制

java

复制

```java
try {
    // 可能抛出异常的代码
    FileInputStream fis = new FileInputStream("test.txt");
} catch (FileNotFoundException e) {
    // 处理特定异常
    System.out.println("文件未找到");
} catch (Exception e) {
    // 处理其他异常
    e.printStackTrace();
} finally {
    // 无论是否发生异常都会执行
    System.out.println("清理工作");
}
```

### 3. 自定义异常

java

复制

```java
public class MyException extends Exception {
    public MyException(String message) {
        super(message);
    }
}

// 使用
throw new MyException("自定义异常信息");
```

## 四、集合框架

### 1. 主要接口

- Collection
  - List (有序可重复)
  - Set (无序不重复)
  - Queue (队列)
- Map (键值对)

### 2. 常用实现类

java

复制

```java
List<String> arrayList = new ArrayList<>(); // 数组实现
List<String> linkedList = new LinkedList<>(); // 链表实现

Set<Integer> hashSet = new HashSet<>(); // 哈希表实现
Set<Integer> treeSet = new TreeSet<>(); // 红黑树实现

Map<String, Integer> hashMap = new HashMap<>(); // 哈希表实现
Map<String, Integer> treeMap = new TreeMap<>(); // 红黑树实现
```

### 3. 集合遍历

java

复制

```java
// List遍历
for (String item : arrayList) {
    System.out.println(item);
}

// Map遍历
for (Map.Entry<String, Integer> entry : hashMap.entrySet()) {
    System.out.println(entry.getKey() + ": " + entry.getValue());
}
```

## 五、IO流

### 1. 字节流

java

复制

```java
// 文件复制
try (InputStream in = new FileInputStream("source.txt");
     OutputStream out = new FileOutputStream("target.txt")) {
    byte[] buffer = new byte[1024];
    int length;
    while ((length = in.read(buffer)) != -1) {
        out.write(buffer, 0, length);
    }
} catch (IOException e) {
    e.printStackTrace();
}
```

### 2. 字符流

java

复制

```java
// 读取文本文件
try (BufferedReader reader = new BufferedReader(new FileReader("test.txt"))) {
    String line;
    while ((line = reader.readLine()) != null) {
        System.out.println(line);
    }
} catch (IOException e) {
    e.printStackTrace();
}
```

## 六、多线程

### 1. 创建线程的方式

java

复制

```java
// 方式1: 继承Thread类
class MyThread extends Thread {
    public void run() {
        System.out.println("线程运行中");
    }
}

// 方式2: 实现Runnable接口
class MyRunnable implements Runnable {
    public void run() {
        System.out.println("线程运行中");
    }
}

// 启动线程
new MyThread().start();
new Thread(new MyRunnable()).start();
```

### 2. 线程同步

java

复制

```java
// 同步方法
public synchronized void add(int value) {
    this.count += value;
}

// 同步代码块
public void add(int value) {
    synchronized(this) {
        this.count += value;
    }
}

// 使用Lock
private Lock lock = new ReentrantLock();

public void add(int value) {
    lock.lock();
    try {
        this.count += value;
    } finally {
        lock.unlock();
    }
}
```

### 3. 线程池

java

复制

```java
ExecutorService executor = Executors.newFixedThreadPool(5);
executor.submit(() -> {
    System.out.println("任务执行中");
});
executor.shutdown();
```

## 七、Java新特性

### 1. Lambda表达式

java

复制

```java
List<String> names = Arrays.asList("Tom", "Jerry", "Spike");

// 传统方式
Collections.sort(names, new Comparator<String>() {
    public int compare(String a, String b) {
        return a.compareTo(b);
    }
});

// Lambda方式
Collections.sort(names, (a, b) -> a.compareTo(b));
```

### 2. Stream API

java

复制

```java
List<String> filtered = names.stream()
    .filter(s -> s.startsWith("J"))
    .map(String::toUpperCase)
    .collect(Collectors.toList());
```

### 3. 模块化(Java 9+)

java

复制

```java
module com.example.myapp {
    requires java.base;
    requires java.sql;
    exports com.example.mypackage;
}
```

## 八、JVM基础

### 1. 内存区域

- 方法区(Method Area)
- 堆(Heap)
- 虚拟机栈(VM Stack)
- 本地方法栈(Native Method Stack)
- 程序计数器(Program Counter Register)

### 2. 类加载机制

1. 加载(Loading)
2. 验证(Verification)
3. 准备(Preparation)
4. 解析(Resolution)
5. 初始化(Initialization)

### 3. GC机制

- 分代收集
- 标记-清除
- 标记-整理
- 复制算法

## 九、设计模式

### 1. 单例模式

java

复制

```java
public class Singleton {
    private static volatile Singleton instance;
    
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

### 2. 工厂模式

java

复制

```java
public interface Shape {
    void draw();
}

public class Circle implements Shape {
    public void draw() {
        System.out.println("画圆形");
    }
}

public class ShapeFactory {
    public Shape getShape(String type) {
        if ("circle".equalsIgnoreCase(type)) {
            return new Circle();
        }
        return null;
    }
}
```

## 十、最佳实践

1. **代码规范**
   - 遵循命名规范
   - 适当添加注释
   - 保持方法短小精悍
2. **性能优化**
   - 避免创建不必要的对象
   - 使用StringBuilder处理字符串拼接
   - 合理使用集合类
3. **安全编码**
   - 防止SQL注入
   - 处理敏感数据
   - 验证用户输入

Java的这些核心概念构成了Java编程的基础，掌握它们对于成为一名优秀的Java开发者至关重要。随着Java版本的更新，新的特性不断加入，开发者也需要持续学习和适应这些变化。