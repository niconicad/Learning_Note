C++ 中的 Lambda 表达式是 C++11 引入的一个重要特性，它提供了一种简洁的方式来表示匿名函数（即没有名称的函数）。Lambda 表达式可以捕获上下文变量，并且可以像普通函数一样调用。以下是 C++ Lambda 表达式的总结：

---

### 1. **Lambda 表达式的基本语法**
Lambda 表达式的基本语法如下：
```cpp
[capture](parameters) -> return_type {
    // 函数体
}
```

- **`capture`**：捕获列表，用于指定 Lambda 表达式可以访问的外部变量。
- **`parameters`**：参数列表，与普通函数的参数列表类似。
- **`return_type`**：返回类型（可选）。如果省略，编译器会自动推导返回类型。
- **`函数体`**：Lambda 表达式的实现代码。

---

### 2. **Lambda 表达式的示例**

#### **示例 1：最简单的 Lambda 表达式**
```cpp
auto greet = []() {
    std::cout << "Hello, World!" << std::endl;
};
greet();  // 输出: Hello, World!
```

- 这是一个无参数、无返回值的 Lambda 表达式。
- `auto` 关键字用于自动推导 Lambda 表达式的类型。

#### **示例 2：带参数的 Lambda 表达式**
```cpp
auto add = [](int a, int b) {
    return a + b;
};
std::cout << add(3, 4) << std::endl;  // 输出: 7
```

- 这是一个带两个参数并返回 `int` 类型的 Lambda 表达式。

#### **示例 3：指定返回类型**
```cpp
auto divide = [](double a, double b) -> double {
    if (b == 0) {
        return 0;  // 避免除零错误
    }
    return a / b;
};
std::cout << divide(10.0, 2.0) << std::endl;  // 输出: 5
```

- 这是一个带两个参数并显式指定返回类型为 `double` 的 Lambda 表达式。

---

### 3. **捕获列表的使用**
捕获列表用于指定 Lambda 表达式可以访问的外部变量。捕获方式有以下几种：

#### **值捕获**
```cpp
int x = 10;
auto lambda = [x]() {
    std::cout << "x = " << x << std::endl;
};
x = 20;  // 修改外部变量
lambda();  // 输出: x = 10
```

- 值捕获会复制外部变量的值，Lambda 表达式内部使用的是捕获时的值。

#### **引用捕获**
```cpp
int x = 10;
auto lambda = [&x]() {
    std::cout << "x = " << x << std::endl;
};
x = 20;  // 修改外部变量
lambda();  // 输出: x = 20
```

- 引用捕获会捕获外部变量的引用，Lambda 表达式内部使用的是最新的值。

#### **隐式捕获**
```cpp
int x = 10;
int y = 20;
auto lambda = [=]() {  // 值捕获所有外部变量
    std::cout << "x = " << x << ", y = " << y << std::endl;
};
auto lambda2 = [&]() {  // 引用捕获所有外部变量
    std::cout << "x = " << x << ", y = " << y << std::endl;
};
```

- `[=]`：值捕获所有外部变量。
- `[&]`：引用捕获所有外部变量。

#### **混合捕获**
```cpp
int x = 10;
int y = 20;
auto lambda = [&x, y]() {
    std::cout << "x = " << x << ", y = " << y << std::endl;
};
x = 30;
y = 40;
lambda();  // 输出: x = 30, y = 20
```

- 可以混合使用值捕获和引用捕获。

---

### 4. **Lambda 表达式的应用场景**

#### **作为函数参数**
Lambda 表达式可以作为函数参数传递，常用于标准库算法（如 `std::sort`、`std::for_each`）。

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    std::vector<int> numbers = {3, 1, 4, 1, 5, 9};

    // 使用 Lambda 表达式排序
    std::sort(numbers.begin(), numbers.end(), [](int a, int b) {
        return a < b;
    });

    // 使用 Lambda 表达式打印
    std::for_each(numbers.begin(), numbers.end(), [](int n) {
        std::cout << n << " ";
    });

    return 0;
}
```

#### **作为返回值**
Lambda 表达式可以作为函数的返回值。

```cpp
auto make_multiplier = [](int factor) {
    return [factor](int x) { return x * factor; };
};

auto double_value = make_multiplier(2);
std::cout << double_value(5) << std::endl;  // 输出: 10
```

---

### 5. **Lambda 表达式的类型**
Lambda 表达式的类型是一个唯一的、匿名的函数对象类型。如果需要存储 Lambda 表达式，可以使用 `auto` 或 `std::function`。

#### **使用 `auto`**
```cpp
auto lambda = []() {
    std::cout << "Hello, Lambda!" << std::endl;
};
lambda();
```

#### **使用 `std::function`**
```cpp
#include <functional>

std::function<void()> lambda = []() {
    std::cout << "Hello, Lambda!" << std::endl;
};
lambda();
```

---

### 6. **总结**
- **语法**：`[capture](parameters) -> return_type { ... }`。
- **捕获列表**：支持值捕获、引用捕获、隐式捕获和混合捕获。
- **应用场景**：适合作为函数参数、返回值或临时函数对象。
- **类型**：Lambda 表达式的类型是唯一的匿名类型，可以使用 `auto` 或 `std::function` 存储。

Lambda 表达式是 C++ 中强大的匿名函数工具，极大地简化了代码并支持函数式编程风格。如果你有其他问题，欢迎继续提问！