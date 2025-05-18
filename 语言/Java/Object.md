在 Java 中，`Object` 类是所有类的根类，所有类都直接或间接继承自 `Object`。`Object` 类提供了一些通用的方法和属性，这些方法可以被所有 Java 对象使用。以下是 `Object` 类的主要方法和属性的汇总：

---

### **1. `Object` 类的方法**

#### **(1) `public final Class<?> getClass()`**
- **作用**：返回对象的运行时类（`Class` 对象）。
- **示例**：
  ```java
  String str = "Hello";
  Class<?> clazz = str.getClass(); // 返回 String.class
  ```

#### **(2) `public int hashCode()`**
- **作用**：返回对象的哈希码值（用于哈希表，如 `HashMap`）。
- **规则**：
  - 如果两个对象通过 `equals()` 方法相等，则它们的 `hashCode()` 必须相同。
  - 默认实现通常返回对象的内存地址。
- **示例**：
  ```java
  String str = "Hello";
  int hashCode = str.hashCode(); // 返回字符串的哈希码
  ```

#### **(3) `public boolean equals(Object obj)`**
- **作用**：比较两个对象是否相等。
- **规则**：
  - 默认实现比较对象的内存地址（`==`）。
  - 通常需要重写以实现逻辑相等性（如比较对象的内容）。
- **示例**：
  ```java
  String str1 = "Hello";
  String str2 = "Hello";
  boolean isEqual = str1.equals(str2); // true
  ```

#### **(4) `public String toString()`**
- **作用**：返回对象的字符串表示。
- **默认实现**：返回 `类名@哈希码`（如 `java.lang.Object@1b6d3586`）。
- **通常需要重写**以提供更有意义的描述。
- **示例**：
  ```java
  String str = "Hello";
  System.out.println(str.toString()); // 输出 "Hello"
  ```

#### **(5) `protected Object clone() throws CloneNotSupportedException`**
- **作用**：创建并返回当前对象的副本（浅拷贝）。
- **注意**：
  - 需要实现 `Cloneable` 接口，否则会抛出 `CloneNotSupportedException`。
  - 默认实现是浅拷贝，引用类型的字段不会被递归复制。
- **示例**：
  ```java
  class MyClass implements Cloneable {
      public int value;
      @Override
      protected Object clone() throws CloneNotSupportedException {
          return super.clone();
      }
  }
  ```

#### **(6) `protected void finalize() throws Throwable`**
- **作用**：在对象被垃圾回收之前调用。
- **注意**：
  - 不推荐使用，因为垃圾回收的时间不确定。
  - 在 Java 9 中已被标记为弃用（`@Deprecated`）。
- **示例**：
  ```java
  @Override
  protected void finalize() throws Throwable {
      System.out.println("Finalize called");
  }
  ```

#### **(7) `public final void wait() throws InterruptedException`**
- **作用**：使当前线程等待，直到另一个线程调用 `notify()` 或 `notifyAll()`。
- **注意**：必须在同步代码块或同步方法中调用。
- **示例**：
  ```java
  synchronized (obj) {
      obj.wait(); // 当前线程等待
  }
  ```

#### **(8) `public final void wait(long timeout) throws InterruptedException`**
- **作用**：使当前线程等待，直到超时或另一个线程调用 `notify()` 或 `notifyAll()`。
- **示例**：
  ```java
  synchronized (obj) {
      obj.wait(1000); // 等待 1 秒
  }
  ```

#### **(9) `public final void wait(long timeout, int nanos) throws InterruptedException`**
- **作用**：与 `wait(long timeout)` 类似，但支持纳秒级精度。
- **示例**：
  ```java
  synchronized (obj) {
      obj.wait(1000, 500000); // 等待 1.5 秒
  }
  ```

#### **(10) `public final void notify()`**
- **作用**：唤醒一个等待当前对象锁的线程。
- **注意**：必须在同步代码块或同步方法中调用。
- **示例**：
  ```java
  synchronized (obj) {
      obj.notify(); // 唤醒一个等待线程
  }
  ```

#### **(11) `public final void notifyAll()`**
- **作用**：唤醒所有等待当前对象锁的线程。
- **注意**：必须在同步代码块或同步方法中调用。
- **示例**：
  ```java
  synchronized (obj) {
      obj.notifyAll(); // 唤醒所有等待线程
  }
  ```

---

### **2. `Object` 类的属性**
`Object` 类本身没有定义任何属性（字段），它是一个纯粹的基类，仅提供方法。

---

### **3. 总结**
| 方法名                          | 作用描述                                                     |
| ------------------------------- | ------------------------------------------------------------ |
| `getClass()`                    | 返回对象的运行时类（`Class` 对象）。                         |
| `hashCode()`                    | 返回对象的哈希码值。                                         |
| `equals(Object obj)`            | 比较两个对象是否相等。                                       |
| `toString()`                    | 返回对象的字符串表示。                                       |
| `clone()`                       | 创建并返回对象的副本（浅拷贝）。                             |
| `finalize()`                    | 在对象被垃圾回收之前调用（不推荐使用）。                     |
| `wait()`                        | 使当前线程等待，直到另一个线程调用 `notify()` 或 `notifyAll()`。 |
| `wait(long timeout)`            | 使当前线程等待，直到超时或另一个线程调用 `notify()` 或 `notifyAll()`。 |
| `wait(long timeout, int nanos)` | 支持纳秒级精度的等待。                                       |
| `notify()`                      | 唤醒一个等待当前对象锁的线程。                               |
| `notifyAll()`                   | 唤醒所有等待当前对象锁的线程。                               |

- `Object` 类的方法为所有 Java 对象提供了基础功能。
- 常用的方法包括 `equals()`、`hashCode()`、`toString()` 等，通常需要根据业务需求重写。
- 多线程相关方法（如 `wait()`、`notify()`）需要在同步代码块中使用。