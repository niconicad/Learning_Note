Java 中的 Lambda 表达式是 Java 8 引入的一个重要特性，它提供了一种简洁的方式来表示匿名函数（即没有名称的函数）。Lambda 表达式主要用于简化函数式接口的实现，使得代码更加简洁和易读。以下是 Java Lambda 表达式的总结：

---

### 1. **Lambda 表达式的基本语法**
Lambda 表达式的基本语法如下：
```java
(parameters) -> expression
```
或
```java
(parameters) -> { statements; }
```

- **`parameters`**：参数列表，可以为空或包含多个参数。
- **`->`**：Lambda 操作符，将参数和表达式或语句块分开。
- **`expression`**：单个表达式，Lambda 表达式的返回值。
- **`{ statements; }`**：语句块，可以包含多条语句。

---

### 2. **Lambda 表达式的示例**

#### **示例 1：无参数**
```java
Runnable runnable = () -> System.out.println("Hello, Lambda!");
runnable.run();  // 输出: Hello, Lambda!
```

#### **示例 2：单个参数**
```java
Consumer<String> consumer = (name) -> System.out.println("Hello, " + name);
consumer.accept("Alice");  // 输出: Hello, Alice
```

#### **示例 3：多个参数**
```java
BinaryOperator<Integer> add = (a, b) -> a + b;
System.out.println(add.apply(3, 4));  // 输出: 7
```

#### **示例 4：语句块**
```java
BinaryOperator<Integer> max = (a, b) -> {
    if (a > b) {
        return a;
    } else {
        return b;
    }
};
System.out.println(max.apply(5, 10));  // 输出: 10
```

---

### 3. **Lambda 表达式的使用场景**
Lambda 表达式主要用于实现**函数式接口**（即只有一个抽象方法的接口）。常见的函数式接口包括：
- `Runnable`：无参数，无返回值。
- `Consumer<T>`：接受一个参数，无返回值。
- `Supplier<T>`：无参数，返回一个值。
- `Function<T, R>`：接受一个参数，返回一个值。
- `Predicate<T>`：接受一个参数，返回布尔值。
- `BinaryOperator<T>`：接受两个参数，返回一个值。

---

### 4. **Lambda 表达式的类型推断**
Java 编译器可以根据上下文推断 Lambda 表达式的参数类型。例如：
```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
names.forEach(name -> System.out.println(name));  // 输出: Alice Bob Charlie
```

- 在这里，`name` 的类型被推断为 `String`。

---

### 5. **方法引用**
方法引用是 Lambda 表达式的一种简化形式，用于直接引用已有的方法。方法引用的语法如下：
- **静态方法引用**：`ClassName::staticMethod`
- **实例方法引用**：`instance::instanceMethod`
- **构造方法引用**：`ClassName::new`

#### **示例**
```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
names.forEach(System.out::println);  // 输出: Alice Bob Charlie
```

---

### 6. **Lambda 表达式的变量捕获**
Lambda 表达式可以捕获外部变量，但有以下限制：
- **局部变量**：必须是 `final` 或事实上 `final`（即不可变）。
- **实例变量和静态变量**：可以修改。

#### **示例**
```java
int x = 10;
Runnable runnable = () -> System.out.println(x);  // x 必须是 final 或事实上 final
runnable.run();  // 输出: 10
```

---

### 7. **Lambda 表达式的优点**
- **简洁**：减少了样板代码，使代码更易读。
- **函数式编程**：支持函数式编程风格，如高阶函数和流操作。
- **并行处理**：与 Stream API 结合，可以方便地实现并行处理。

---

### 8. **Lambda 表达式的局限性**
- **只能用于函数式接口**：Lambda 表达式只能用于实现只有一个抽象方法的接口。
- **调试困难**：由于 Lambda 表达式是匿名的，调试时可能不如普通方法直观。

---

### 9. **总结**
- **语法**：`(parameters) -> expression` 或 `(parameters) -> { statements; }`。
- **使用场景**：主要用于实现函数式接口。
- **方法引用**：简化 Lambda 表达式，直接引用已有方法。
- **变量捕获**：可以捕获外部变量，但局部变量必须是 `final` 或事实上 `final`。

Lambda 表达式是 Java 8 引入的强大特性，极大地简化了代码，并支持函数式编程风格。如果你有其他问题，欢迎继续提问！