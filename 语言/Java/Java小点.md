# 小点

## - 为什么修改equals()方法时也要修改hashCode（）方法?

- 前者判断相等的地方后者必须也相等，否则HashSet等会出问题

## - Native方法？

- 使用c++或者C来实现





## - 重写equals()和hashCode()

在 Java 中，重写 `equals()` 和 `hashCode()` 方法是非常重要的，尤其是在使用集合类（如 `HashMap`、`HashSet`）时。为了确保对象在逻辑上相等时能够正确工作，必须遵循以下规则：

1. **`equals()` 规则**：
   - 自反性：`x.equals(x)` 必须为 `true`。
   - 对称性：如果 `x.equals(y)` 为 `true`，则 `y.equals(x)` 也必须为 `true`。
   - 传递性：如果 `x.equals(y)` 为 `true` 且 `y.equals(z)` 为 `true`，则 `x.equals(z)` 也必须为 `true`。
   - 一致性：多次调用 `x.equals(y)` 应该始终返回相同的结果。
   - 非空性：`x.equals(null)` 必须为 `false`。

2. **`hashCode()` 规则**：
   - 如果两个对象通过 `equals()` 方法相等，则它们的 `hashCode()` 必须相同。
   - 如果两个对象通过 `equals()` 方法不相等，它们的 `hashCode()` 可以相同，但最好不同（以减少哈希冲突）。

### **示例：重写 `equals()` 和 `hashCode()`**

假设我们有一个 `Person` 类，包含 `name` 和 `age` 两个字段。我们希望两个 `Person` 对象在 `name` 和 `age` 都相等时被认为是相等的。

```java
import java.util.Objects;

public class Person {
    private String name;
    private int age;

    // 构造方法
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // 重写 equals 方法
    @Override
    public boolean equals(Object obj) {
        // 1. 检查是否是同一个对象
        if (this == obj) {
            return true;
        }
        // 2. 检查对象是否为 null 或类型是否不匹配
        if (obj == null || getClass() != obj.getClass()) {
            return false;
        }
        // 3. 类型转换
        Person person = (Person) obj;
        // 4. 比较字段值
        return age == person.age && Objects.equals(name, person.name);
    }

    // 重写 hashCode 方法
    @Override
    public int hashCode() {
        // 使用 Objects.hash() 方法生成哈希码
        return Objects.hash(name, age);
    }

    // 重写 toString 方法（可选）
    @Override
    public String toString() {
        return "Person{name='" + name + "', age=" + age + "}";
    }

    // 测试
    public static void main(String[] args) {
        Person person1 = new Person("Alice", 25);
        Person person2 = new Person("Alice", 25);
        Person person3 = new Person("Bob", 30);

        // 测试 equals 方法
        System.out.println("person1.equals(person2): " + person1.equals(person2)); // true
        System.out.println("person1.equals(person3): " + person1.equals(person3)); // false

        // 测试 hashCode 方法
        System.out.println("person1.hashCode(): " + person1.hashCode()); // 相同
        System.out.println("person2.hashCode(): " + person2.hashCode()); // 相同
        System.out.println("person3.hashCode(): " + person3.hashCode()); // 不同
    }
}
```

---

### **代码解析**

#### **1. `equals()` 方法**
- **步骤 1**：检查是否是同一个对象（`this == obj`），如果是，直接返回 `true`。
- **步骤 2**：检查对象是否为 `null` 或类型是否不匹配（`getClass() != obj.getClass()`），如果是，返回 `false`。
- **步骤 3**：将对象转换为当前类型（`Person`）。
- **步骤 4**：比较字段值（`name` 和 `age`），使用 `Objects.equals()` 方法避免空指针异常。

#### **2. `hashCode()` 方法**
- 使用 `Objects.hash()` 方法生成哈希码，该方法会根据传入的字段值计算哈希值。
- 确保 `equals()` 相等的对象具有相同的哈希码。

#### **3. `toString()` 方法（可选）**
- 重写 `toString()` 方法以提供更有意义的对象描述。

---

### **测试结果**
- `person1.equals(person2)` 返回 `true`，因为 `name` 和 `age` 都相等。
- `person1.equals(person3)` 返回 `false`，因为 `name` 和 `age` 不相等。
- `person1.hashCode()` 和 `person2.hashCode()` 相同，因为它们的字段值相同。
- `person3.hashCode()` 不同，因为字段值不同。

---

### **注意事项**
1. **一致性**：确保 `equals()` 和 `hashCode()` 的逻辑一致。
2. **不可变字段**：如果对象是哈希表的键，最好使用不可变字段计算哈希码。
3. **性能**：`hashCode()` 的计算应尽量高效，避免复杂计算。
4. **工具支持**：可以使用 IDE（如 IntelliJ IDEA 或 Eclipse）自动生成 `equals()` 和 `hashCode()` 方法。

---

通过以上示例和解析，你可以正确重写 `equals()` 和 `hashCode()` 方法，确保对象在逻辑相等时能够正确工作。



## - getClass()和instanceof比较

在 Java 中，`getClass()` 和 `instanceof` 都用于检查对象的类型，但它们的用途和行为有显著区别。以下是它们的详细比较：

---

### **1. `getClass()`**
- **作用**：返回对象的运行时类（`Class` 对象）。
- **特点**：
  - 精确匹配对象的实际类型。
  - 不考虑继承关系。
- **语法**：
  ```java
  public final Class<?> getClass()
  ```
- **示例**：
  ```java
  Object obj = "Hello";
  System.out.println(obj.getClass()); // 输出 class java.lang.String
  ```

---

### **2. `instanceof`**
- **作用**：检查对象是否是某个类或其子类的实例。
- **特点**：
  - 考虑继承关系。
  - 可以检查接口实现。
- **语法**：
  ```java
  object instanceof Type
  ```
- **示例**：
  ```java
  Object obj = "Hello";
  System.out.println(obj instanceof String); // 输出 true
  System.out.println(obj instanceof Object); // 输出 true
  ```

---

### **3. 主要区别**

| 特性         | `getClass()`               | `instanceof`                       |
| ------------ | -------------------------- | ---------------------------------- |
| **精确性**   | 精确匹配对象的实际类型。   | 检查对象是否是指定类型或其子类型。 |
| **继承关系** | 不考虑继承关系。           | 考虑继承关系。                     |
| **接口检查** | 不能直接检查接口。         | 可以检查接口实现。                 |
| **性能**     | 通常比 `instanceof` 更快。 | 稍慢，因为需要检查继承链。         |
| **适用场景** | 需要精确匹配类型时使用。   | 需要检查类型或子类型时使用。       |

---

### **4. 使用场景**

#### **(1) 使用 `getClass()` 的场景**
- 需要精确匹配对象的类型。
- 在重写 `equals()` 方法时，通常使用 `getClass()` 确保类型严格匹配：
  ```java
  @Override
  public boolean equals(Object obj) {
      if (obj == null || getClass() != obj.getClass()) {
          return false;
      }
      // 其他比较逻辑
  }
  ```

#### **(2) 使用 `instanceof` 的场景**
- 需要检查对象是否是指定类型或其子类型。
- 在处理多态或接口时使用：
  ```java
  if (obj instanceof Runnable) {
      ((Runnable) obj).run();
  }
  ```

---

### **5. 示例对比**

#### **示例 1：`getClass()`**
```java
class Animal {}
class Dog extends Animal {}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Dog();
        System.out.println(animal.getClass()); // 输出 class Dog
        System.out.println(animal.getClass() == Animal.class); // 输出 false
    }
}
```
- `getClass()` 返回对象的实际类型（`Dog`），而不是引用类型（`Animal`）。

#### **示例 2：`instanceof`**
```java
class Animal {}
class Dog extends Animal {}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Dog();
        System.out.println(animal instanceof Dog); // 输出 true
        System.out.println(animal instanceof Animal); // 输出 true
    }
}
```
- `instanceof` 检查对象是否是指定类型或其子类型。

---

### **6. 注意事项**

#### **(1) `getClass()` 的局限性**
- 不能用于检查接口实现。
- 在继承关系中，`getClass()` 只能精确匹配对象的实际类型。

#### **(2) `instanceof` 的局限性**
- 不能精确匹配对象的实际类型。
- 如果对象为 `null`，`instanceof` 返回 `false`，而 `getClass()` 会抛出 `NullPointerException`。

#### **(3) 性能考虑**
- `getClass()` 通常比 `instanceof` 更快，因为 `instanceof` 需要检查继承链。

#### **(4) 在 `equals()` 中的选择**
- 如果类不是 `final`，建议使用 `getClass()` 确保类型严格匹配。
- 如果类是 `final`，可以使用 `instanceof`。

---

### **7. 总结**

| 特性         | `getClass()`               | `instanceof`                       |
| ------------ | -------------------------- | ---------------------------------- |
| **精确性**   | 精确匹配对象的实际类型。   | 检查对象是否是指定类型或其子类型。 |
| **继承关系** | 不考虑继承关系。           | 考虑继承关系。                     |
| **接口检查** | 不能直接检查接口。         | 可以检查接口实现。                 |
| **性能**     | 通常比 `instanceof` 更快。 | 稍慢，因为需要检查继承链。         |
| **适用场景** | 需要精确匹配类型时使用。   | 需要检查类型或子类型时使用。       |

- 在重写 `equals()` 方法时，通常使用 `getClass()` 确保类型严格匹配。
- 在处理多态或接口时，使用 `instanceof` 更灵活。





## - 使用StringBuilder来进行字符串拼接而不是“+”，因为会多出不必要的开销

~~~java
String[] arr = {"he", "llo", "world"};
StringBuilder s = new StringBuilder();
for (String value : arr) {
    s.append(value);
}
System.out.println(s);
~~~



## - Object中的equals（）对比的是对象的地址，而String类中的是比较值（重写过）



## - StringBuffer和StringBuilder对比

`StringBuilder` 和 `StringBuffer` 是 Java 中用于处理字符串的两个类，它们都提供了可变的字符串操作功能。以下是它们的主要区别：

### 1. 线程安全性
- **StringBuffer**：是线程安全的，所有方法都使用了 `synchronized` 关键字进行同步，确保在多线程环境下的安全性。
- **StringBuilder**：不是线程安全的，没有使用同步机制，因此在单线程环境下性能更高。

### 2. 性能
- **StringBuilder**：由于没有同步开销，性能通常优于 `StringBuffer`，尤其是在单线程环境下。
- **StringBuffer**：由于同步机制的存在，性能相对较低，但在多线程环境下更安全。

### 3. 使用场景
- **StringBuilder**：适用于单线程环境，或者在明确知道不会有多线程竞争的情况下使用。
- **StringBuffer**：适用于多线程环境，或者在需要确保线程安全的情况下使用。

### 4. API 兼容性
- 两者的 API 几乎完全相同，主要区别在于线程安全性。因此，在大多数情况下，可以很容易地在两者之间切换。

### 示例代码
```java
// 使用 StringBuilder
StringBuilder sb = new StringBuilder();
sb.append("Hello");
sb.append(" World");
System.out.println(sb.toString()); // 输出: Hello World

// 使用 StringBuffer
StringBuffer sbf = new StringBuffer();
sbf.append("Hello");
sbf.append(" World");
System.out.println(sbf.toString()); // 输出: Hello World
```

### 总结
- 如果你在单线程环境下工作，并且追求更高的性能，推荐使用 `StringBuilder`。
- 如果你在多线程环境下工作，或者需要确保线程安全，推荐使用 `StringBuffer`。

选择哪个类取决于你的具体需求和环境。



## - 常量折叠：在编译时已经确定的值会变为常量直接写入



## - 字符串常量池

**字符串常量池（String Pool）** 是 Java 中用于存储字符串常量的特殊内存区域，它是 **方法区（Method Area）** 的一部分。在 Java 8 及之前，方法区是 **永久代（PermGen）** 的一部分；而在 Java 8 及之后，方法区被 **元空间（Metaspace）** 取代，但字符串常量池仍然存在于堆内存（Heap）中。

---

### 字符串常量池的位置
1. **Java 7 之前**：
   - 字符串常量池位于 **永久代（PermGen）** 中。
   - 永久代是方法区的一部分，用于存储类信息、常量池、静态变量等。
   - 问题：永久代大小有限，容易导致 `OutOfMemoryError`。

2. **Java 7 及之后**：
   - 字符串常量池被移动到 **堆内存（Heap）** 中。
   - 堆内存的大小可以通过 JVM 参数动态调整，避免了永久代的限制。
   - 优点：减少了 `OutOfMemoryError` 的风险，同时垃圾回收器可以管理字符串常量池中的对象。

3. **Java 8 及之后**：
   - 永久代被彻底移除，方法区由 **元空间（Metaspace）** 替代。
   - 字符串常量池仍然位于堆内存中。

---

### 字符串常量池的作用
- 字符串常量池是为了提高性能和减少内存消耗而设计的。
- 当创建一个字符串常量时，JVM 会首先检查字符串常量池中是否已经存在相同的字符串：
  - 如果存在，则直接返回常量池中的引用。
  - 如果不存在，则在常量池中创建一个新的字符串对象，并返回其引用。

---

### 示例代码
```java
String s1 = "Hello"; // 字符串常量池中创建 "Hello"
String s2 = "Hello"; // 直接引用常量池中的 "Hello"
String s3 = new String("Hello"); // 在堆中创建一个新的字符串对象

System.out.println(s1 == s2); // true，引用相同
System.out.println(s1 == s3); // false，引用不同
```

---

### 字符串常量池的特点
1. **节省内存**：
   - 相同的字符串常量只存储一份，避免重复创建。

2. **提高性能**：
   - 通过直接引用常量池中的字符串，减少对象创建和垃圾回收的开销。

3. **不可变性**：
   - 字符串常量池中的字符串是不可变的（immutable），任何修改都会创建一个新的字符串对象。

---

### 字符串常量池的存储内容
- 字符串常量池存储的是 **字符串常量**，即通过双引号直接定义的字符串。
- 例如：
  ```java
  String s1 = "Hello"; // "Hello" 存储在字符串常量池中
  String s2 = new String("Hello"); // "Hello" 存储在堆中，但常量池中也会存储 "Hello"
  ```

---

### 字符串常量池与 `intern()` 方法
- `intern()` 方法用于将字符串对象添加到字符串常量池中（如果池中不存在），并返回常量池中的引用。
- 示例：
  ```java
  String s1 = new String("Hello"); // 在堆中创建对象
  String s2 = s1.intern(); // 将 "Hello" 添加到常量池（如果不存在），并返回引用
  String s3 = "Hello"; // 直接引用常量池中的 "Hello"
  
  System.out.println(s1 == s2); // false
  System.out.println(s2 == s3); // true
  ```

---

### 总结
- **Java 7 之前**：字符串常量池位于永久代（PermGen）。
- **Java 7 及之后**：字符串常量池位于堆内存（Heap）。
- **作用**：节省内存、提高性能。
- **特点**：不可变性、共享性。
- **使用场景**：适用于存储字符串常量，避免重复创建。

通过理解字符串常量池的位置和机制，可以更好地优化字符串的使用，避免内存浪费和性能问题。



## -字符串创建例子

这段代码展示了 Java 中字符串常量池和 `intern()` 方法的行为。我们来逐行分析代码，并解释输出结果的原因。

---

### 代码分析
```java
// s1 指向字符串常量池中的 "Java" 对象
String s1 = "Java";
// s2 也指向字符串常量池中的 "Java" 对象，和 s1 是同一个对象
String s2 = s1.intern();
// 在堆中创建一个新的 "Java" 对象，s3 指向它
String s3 = new String("Java");
// s4 指向字符串常量池中的 "Java" 对象，和 s1 是同一个对象
String s4 = s3.intern();
// s1 和 s2 指向的是同一个常量池中的对象
System.out.println(s1 == s2); // true
// s3 指向堆中的对象，s4 指向常量池中的对象，所以不同
System.out.println(s3 == s4); // false
// s1 和 s4 都指向常量池中的同一个对象
System.out.println(s1 == s4); // true
```

---

### 1. **`String s1 = "Java";`**
- `"Java"` 是一个字符串常量，会被放入字符串常量池。
- `s1` 指向常量池中的 `"Java"`。

---

### 2. **`String s2 = s1.intern();`**
- `s1.intern()` 会尝试将 `s1` 的内容（即 `"Java"`）放入字符串常量池。
- 由于 `"Java"` 已经存在于常量池中，`intern()` 方法会直接返回常量池中的引用。
- 因此，`s2` 也指向常量池中的 `"Java"`，和 `s1` 是同一个对象。

---

### 3. **`String s3 = new String("Java");`**
- `new String("Java")` 会在堆内存中创建一个新的字符串对象。
- 虽然 `"Java"` 已经存在于常量池中，但 `new String()` 会强制在堆中创建一个新的对象。
- `s3` 指向堆内存中的新对象。

---

### 4. **`String s4 = s3.intern();`**
- `s3.intern()` 会尝试将 `s3` 的内容（即 `"Java"`）放入字符串常量池。
- 由于 `"Java"` 已经存在于常量池中，`intern()` 方法会直接返回常量池中的引用。
- 因此，`s4` 指向常量池中的 `"Java"`，和 `s1` 是同一个对象。

---

### 5. **`System.out.println(s1 == s2);`**
- `s1` 和 `s2` 都指向常量池中的 `"Java"`。
- `==` 比较的是引用地址，两者指向同一个对象。
- 输出：`true`。

---

### 6. **`System.out.println(s3 == s4);`**
- `s3` 指向堆内存中的新对象。
- `s4` 指向常量池中的 `"Java"`。
- `==` 比较的是引用地址，堆内存和常量池的地址不同。
- 输出：`false`。

---

### 7. **`System.out.println(s1 == s4);`**
- `s1` 和 `s4` 都指向常量池中的 `"Java"`。
- `==` 比较的是引用地址，两者指向同一个对象。
- 输出：`true`。

---

### 总结
| 表达式     | 结果  | 原因                                                         |
| ---------- | ----- | ------------------------------------------------------------ |
| `s1 == s2` | true  | `s1` 和 `s2` 都指向常量池中的同一个对象。                    |
| `s3 == s4` | false | `s3` 指向堆内存中的新对象，`s4` 指向常量池中的对象，地址不同。 |
| `s1 == s4` | true  | `s1` 和 `s4` 都指向常量池中的同一个对象。                    |

---

### 关键点
1. **字符串常量池**：
   - 直接使用双引号定义的字符串（如 `"Java"`）会存储在字符串常量池中。
   - 常量池中的字符串是唯一的，相同的字符串只会存储一份。

2. **`new String()`**：
   - 使用 `new String()` 会在堆内存中创建一个新的字符串对象，即使内容与常量池中的字符串相同。

3. **`intern()` 方法**：
   - `intern()` 方法会尝试将字符串放入常量池：
     - 如果常量池中已经存在相同的字符串，则返回常量池中的引用。
     - 如果不存在，则将字符串添加到常量池，并返回引用。

4. **`==` 和 `equals`**：
   - `==` 比较的是引用地址。
   - `equals` 比较的是字符串内容。如果需要比较内容，应使用 `equals` 方法。



好的！我们来详细分析 `String s3 = new String("Java");` 这行代码的行为，以及它背后的内存分配机制。

---

### 1. **`new String("Java")` 的执行过程**
当使用 `new String("Java")` 创建一个字符串对象时，JVM 会执行以下步骤：

#### 步骤 1：检查字符串常量池
- `"Java"` 是一个字符串字面量（字符串常量）。
- JVM 会首先检查字符串常量池中是否已经存在 `"Java"`：
  - 如果存在，则直接使用常量池中的 `"Java"`。
  - 如果不存在，则在常量池中创建一个新的 `"Java"` 字符串对象。

#### 步骤 2：在堆内存中创建新对象
- `new String("Java")` 会在堆内存中创建一个新的字符串对象。
- 这个新对象的**内容**是从字符串常量池中的 `"Java"` 复制过来的。
- 因此，堆内存中的新对象和常量池中的 `"Java"` 是两个独立的对象，尽管它们的内容相同。

#### 步骤 3：返回堆内存中的对象引用
- `new String("Java")` 返回的是堆内存中新创建的字符串对象的引用。
- 这个引用被赋值给变量 `s3`。

---

### 2. **内存分配示意图**
以下是 `String s3 = new String("Java");` 执行后的内存分配情况：

```
字符串常量池 (String Pool)
+-------------------+
| "Java"            |  <--- 常量池中的 "Java" 对象
+-------------------+

堆内存 (Heap)
+-------------------+
| String对象        |  <--- 堆内存中的新对象，内容为 "Java"
| 内容: "Java"      |
+-------------------+
```

- 常量池中的 `"Java"` 和堆内存中的新对象是两个独立的对象。
- `s3` 指向堆内存中的新对象。

---

### 3. **`new String("Java")` 与 `"Java"` 的区别**
| 特性                | `new String("Java")`           | `"Java"`                       |
| ------------------- | ------------------------------ | ------------------------------ |
| **存储位置**        | 堆内存                         | 字符串常量池                   |
| **对象数量**        | 每次调用都会创建一个新的对象   | 常量池中只存储一份             |
| **引用比较 (`==`)** | 每次创建的对象的引用不同       | 相同内容的字符串引用相同       |
| **性能**            | 较低（每次都在堆中创建新对象） | 较高（直接使用常量池中的对象） |

---

### 4. **代码示例**
```java
String s1 = "Java"; // s1 指向常量池中的 "Java"
String s2 = "Java"; // s2 也指向常量池中的 "Java"
String s3 = new String("Java"); // s3 指向堆内存中的新对象
String s4 = new String("Java"); // s4 指向堆内存中的另一个新对象

System.out.println(s1 == s2); // true，s1 和 s2 指向常量池中的同一个对象
System.out.println(s1 == s3); // false，s1 指向常量池，s3 指向堆内存
System.out.println(s3 == s4); // false，s3 和 s4 是两个不同的堆内存对象
```

---

### 5. **`intern()` 方法的作用**
- `intern()` 方法用于将字符串对象添加到字符串常量池中（如果池中不存在），并返回常量池中的引用。
- 如果常量池中已经存在相同的字符串，则直接返回常量池中的引用。

#### 示例
```java
String s1 = "Java"; // s1 指向常量池中的 "Java"
String s2 = new String("Java"); // s2 指向堆内存中的新对象
String s3 = s2.intern(); // s3 指向常量池中的 "Java"

System.out.println(s1 == s2); // false，s1 指向常量池，s2 指向堆内存
System.out.println(s1 == s3); // true，s1 和 s3 都指向常量池中的同一个对象
```

---

### 6. **总结**
- `new String("Java")` 会在堆内存中创建一个新的字符串对象，即使 `"Java"` 已经存在于字符串常量池中。
- 常量池中的 `"Java"` 和堆内存中的新对象是两个独立的对象。
- `intern()` 方法可以将堆内存中的字符串对象添加到常量池中（如果不存在），并返回常量池中的引用。
- 使用 `new String()` 创建字符串对象会带来额外的内存开销，因此在不需要显式创建新对象时，应优先使用字符串字面量（如 `"Java"`）。

---

### 关键点
1. **`new String("Java")`**：
   - 在堆内存中创建一个新的字符串对象。
   - 内容是从常量池中的 `"Java"` 复制过来的。

2. **字符串常量池**：
   - 存储字符串字面量（如 `"Java"`）。
   - 相同的字符串只会存储一份。

3. **`intern()` 方法**：
   - 将字符串对象添加到常量池中（如果不存在）。
   - 返回常量池中的引用。

4. **性能建议**：
   - 在不需要显式创建新对象时，优先使用字符串字面量（如 `"Java"`）。
   - 避免频繁使用 `new String()`，以减少内存开销。

## - Java不要在try中和finally中同时ruturn，否则会忽略try中的

## -  try with resource 例子

```java
try (BufferedInputStream bin = new BufferedInputStream(new FileInputStream(new File("test.txt")));
     BufferedOutputStream bout = new BufferedOutputStream(new FileOutputStream(new File("out.txt")))) {
    int b;
    while ((b = bin.read()) != -1) {
        bout.write(b);
    }
}
catch (IOException e) {java
    e.printStackTrace();
}
```

会自动关闭需要关闭的资源，而无需在finally中手动关闭

## - **不管是文件读写还是网络发送接收，信息的最小存储单元都是字节，那为什么 I/O 流操作要分为字节流操作和字符流操作呢？**

个人认为主要有两点原因：

- 字符流是由 Java 虚拟机将字节转换得到的，这个过程还算是比较耗时；
- 如果我们不知道编码类型的话，使用字节流的过程中很容易出现乱码问题；



## - 反射会绕过编译时进行的泛型类型检查，从而有安全问题

同时还会破坏封装性，访问私有函数或者变量



