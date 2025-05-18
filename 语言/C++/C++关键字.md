以下是 C++ 中所有关键字的用法、文字解释及示例代码的详细汇总：

---

### 1. **数据类型关键字**
| 关键字     | 用法解释                                 | 示例代码                                                    |
| ---------- | ---------------------------------------- | ----------------------------------------------------------- |
| `int`      | 定义整数类型。                           | ```cpp int num = 10;```                                     |
| `char`     | 定义字符类型。                           | ```cpp char ch = 'A';```                                    |
| `float`    | 定义单精度浮点数类型。                   | ```cpp float num = 3.14f;```                                |
| `double`   | 定义双精度浮点数类型。                   | ```cpp double num = 3.14159;```                             |
| `bool`     | 定义布尔类型，取值为 `true` 或 `false`。 | ```cpp bool flag = true;```                                 |
| `void`     | 表示无类型，通常用于函数返回值或指针。   | ```cpp void myFunction() { }```                             |
| `auto`     | 自动类型推断（C++11 引入）。             | ```cpp auto num = 10; // 推断为 int```                      |
| `decltype` | 获取表达式的类型（C++11 引入）。         | ```cpp int x = 10; decltype(x) y = 20; // y 的类型为 int``` |

---

### 2. **类、结构体和枚举关键字**
| 关键字   | 用法解释                               | 示例代码                                     |
| -------- | -------------------------------------- | -------------------------------------------- |
| `class`  | 定义类。                               | ```cpp class MyClass { };```                 |
| `struct` | 定义结构体。                           | ```cpp struct MyStruct { int x; };```        |
| `enum`   | 定义枚举类型。                         | ```cpp enum MyEnum { VALUE1, VALUE2 };```    |
| `union`  | 定义联合体，所有成员共享同一内存地址。 | ```cpp union MyUnion { int x; float y; };``` |

---

### 3. **访问控制关键字**
| 关键字      | 用法解释                     | 示例代码                                       |
| ----------- | ---------------------------- | ---------------------------------------------- |
| `public`    | 修饰类成员，表示公开访问。   | ```cpp class MyClass { public: int x; };```    |
| `private`   | 修饰类成员，表示私有访问。   | ```cpp class MyClass { private: int x; };```   |
| `protected` | 修饰类成员，表示受保护访问。 | ```cpp class MyClass { protected: int x; };``` |

---

### 4. **函数和成员函数关键字**
| 关键字     | 用法解释                                                 | 示例代码                                  |
| ---------- | -------------------------------------------------------- | ----------------------------------------- |
| `virtual`  | 修饰成员函数，表示虚函数，支持多态。                     | ```cpp virtual void myFunction() { }```   |
| `override` | 修饰成员函数，表示重写基类的虚函数（C++11 引入）。       | ```cpp void myFunction() override { }```  |
| `final`    | 修饰类或成员函数，表示不可继承或不可重写（C++11 引入）。 | ```cpp void myFunction() final { }```     |
| `static`   | 修饰成员函数或变量，表示静态成员，属于类而非实例。       | ```cpp static int myVar = 10;```          |
| `const`    | 修饰成员函数或变量，表示不可修改。                       | ```cpp void myFunction() const { }```     |
| `friend`   | 修饰函数或类，表示友元，可以访问类的私有成员。           | ```cpp friend void myFriendFunction();``` |

---

### 5. **流程控制关键字**
| 关键字     | 用法解释                                         | 示例代码                                                                   |
| ---------- | ------------------------------------------------ | -------------------------------------------------------------------------- |
| `if`       | 条件语句，用于判断条件是否成立。                 | ```cpp if (condition) { /* code */ }```                                    |
| `else`     | 与 `if` 配合使用，表示条件不成立时执行的代码块。 | ```cpp if (condition) { /* code */ } else { /* code */ }```                |
| `switch`   | 多分支选择语句，根据表达式的值选择执行的分支。   | ```cpp switch (value) { case 1: /* code */ break; default: /* code */ }``` |
| `case`     | 与 `switch` 配合使用，表示一个分支条件。         | ```cpp case 1: /* code */ break;```                                        |
| `default`  | 与 `switch` 配合使用，表示默认分支。             | ```cpp default: /* code */```                                              |
| `for`      | 循环语句，用于重复执行代码块。                   | ```cpp for (int i = 0; i < 10; i++) { /* code */ }```                      |
| `while`    | 循环语句，当条件为真时重复执行代码块。           | ```cpp while (condition) { /* code */ }```                                 |
| `do`       | 与 `while` 配合使用，先执行代码块，再判断条件。  | ```cpp do { /* code */ } while (condition);```                             |
| `break`    | 跳出循环或 `switch` 语句。                       | ```cpp while (true) { if (condition) break; }```                           |
| `continue` | 跳过当前循环的剩余代码，进入下一次循环。         | ```cpp for (int i = 0; i < 10; i++) { if (i == 5) continue; }```           |
| `return`   | 从函数中返回值并结束函数执行。                   | ```cpp return 10;```                                                       |

---

### 6. **异常处理关键字**
| 关键字  | 用法解释                   | 示例代码                                                          |
| ------- | -------------------------- | ----------------------------------------------------------------- |
| `try`   | 定义可能抛出异常的代码块。 | ```cpp try { /* code */ } catch (Exception e) { /* handle */ }``` |
| `catch` | 捕获并处理异常。           | ```cpp catch (Exception e) { /* handle */ }```                    |
| `throw` | 手动抛出异常。             | ```cpp throw std::runtime_error("Error");```                      |

---

### 7. **命名空间和模块关键字**
| 关键字      | 用法解释                     | 示例代码                                        |
| ----------- | ---------------------------- | ----------------------------------------------- |
| `namespace` | 定义命名空间，用于组织代码。 | ```cpp namespace MyNamespace { int x = 10; }``` |
| `using`     | 引入命名空间或类型。         | ```cpp using namespace std;```                  |

---

### 8. **模板和泛型编程关键字**
| 关键字     | 用法解释                 | 示例代码                                                          |
| ---------- | ------------------------ | ----------------------------------------------------------------- |
| `template` | 定义模板，支持泛型编程。 | ```cpp template <typename T> T add(T a, T b) { return a + b; }``` |
| `typename` | 用于模板中表示类型参数。 | ```cpp template <typename T> void myFunction() { }```             |

---

### 9. **内存管理关键字**
| 关键字   | 用法解释             | 示例代码                          |
| -------- | -------------------- | --------------------------------- |
| `new`    | 动态分配内存。       | ```cpp int* ptr = new int(10);``` |
| `delete` | 释放动态分配的内存。 | ```cpp delete ptr;```             |

---

### 10. **其他关键字**
| 关键字      | 用法解释                       | 示例代码                          |
| ----------- | ------------------------------ | --------------------------------- |
| `this`      | 表示当前对象的引用。           | ```cpp this->x = 10;```           |
| `sizeof`    | 获取类型或对象的大小。         | ```cpp int size = sizeof(int);``` |
| `typedef`   | 定义类型别名。                 | ```cpp typedef int MyInt;```      |
| `constexpr` | 定义编译时常量（C++11 引入）。 | ```cpp constexpr int x = 10;```   |
| `nullptr`   | 表示空指针（C++11 引入）。     | ```cpp int* ptr = nullptr;```     |

---

### 11. **C++20 新增关键字**
| 关键字     | 用法解释                         | 示例代码                                                                   |
| ---------- | -------------------------------- | -------------------------------------------------------------------------- |
| `concept`  | 定义模板约束（C++20 引入）。     | ```cpp template <typename T> concept Integral = std::is_integral_v<T>;```  |
| `requires` | 定义模板约束条件（C++20 引入）。 | ```cpp template <typename T> requires Integral<T> void myFunction() { }``` |

---

### 总结
以下是 C++ 所有关键字的分类、用法解释及示例代码：

| 分类             | 关键字及用法解释                                                                               | 示例代码 |
| ---------------- | ---------------------------------------------------------------------------------------------- | -------- |
| 数据类型         | `int`, `char`, `float`, `double`, `bool`, `void`, `auto`, `decltype`                           | 见上文   |
| 类、结构体和枚举 | `class`, `struct`, `enum`, `union`                                                             | 见上文   |
| 访问控制         | `public`, `private`, `protected`                                                               | 见上文   |
| 函数和成员函数   | `virtual`, `override`, `final`, `static`, `const`, `friend`                                    | 见上文   |
| 流程控制         | `if`, `else`, `switch`, `case`, `default`, `for`, `while`, `do`, `break`, `continue`, `return` | 见上文   |
| 异常处理         | `try`, `catch`, `throw`                                                                        | 见上文   |
| 命名空间和模块   | `namespace`, `using`                                                                           | 见上文   |
| 模板和泛型编程   | `template`, `typename`                                                                         | 见上文   |
| 内存管理         | `new`, `delete`                                                                                | 见上文   |
| 其他             | `this`, `sizeof`, `typedef`, `constexpr`, `nullptr`                                            | 见上文   |
| C++20 新增       | `concept`, `requires`                                                                          | 见上文   |

通过掌握这些关键字的用法和解释，你可以更好地理解 C++ 语言的特性和编写高效的代码。