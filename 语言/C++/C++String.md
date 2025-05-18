`std::string` 是 C++ 标准库中用于表示和操作字符串的类。它封装了字符数组，并提供了丰富的成员函数来操作字符串。以下是 `std::string` 的常用方法及其简述：

---

## **1. 构造函数**
用于创建 `std::string` 对象。

| 方法                                                | 描述                                                         |
| --------------------------------------------------- | ------------------------------------------------------------ |
| `string()`                                          | 创建一个空字符串。                                           |
| `string(const char* s)`                             | 用 C 风格字符串初始化。                                      |
| `string(const string& str)`                         | 用另一个 `string` 对象初始化。                               |
| `string(size_t n, char c)`                          | 用 `n` 个字符 `c` 初始化。                                   |
| `string(const char* s, size_t n)`                   | 用 C 风格字符串的前 `n` 个字符初始化。                       |
| `string(const string& str, size_t pos, size_t len)` | 用另一个 `string` 对象的子串初始化，从 `pos` 开始，长度为 `len`。 |

**示例**：
```cpp
std::string str1;                // 空字符串
std::string str2("Hello");       // 用 C 风格字符串初始化
std::string str3(str2);          // 用另一个 string 对象初始化
std::string str4(5, 'a');        // 用 5 个 'a' 初始化
std::string str5("Hello World", 5); // 用前 5 个字符初始化
std::string str6(str2, 1, 3);    // 用 str2 的子串初始化，从位置 1 开始，长度为 3
```

---

## **2. 赋值操作**
用于给 `std::string` 对象赋值。

| 方法                                   | 描述                         |
| -------------------------------------- | ---------------------------- |
| `string& operator=(const string& str)` | 用另一个 `string` 对象赋值。 |
| `string& operator=(const char* s)`     | 用 C 风格字符串赋值。        |
| `string& operator=(char c)`            | 用单个字符赋值。             |
| `string& assign(const string& str)`    | 用另一个 `string` 对象赋值。 |
| `string& assign(const char* s)`        | 用 C 风格字符串赋值。        |
| `string& assign(size_t n, char c)`     | 用 `n` 个字符 `c` 赋值。     |

**示例**：
```cpp
std::string str;
str = "Hello";              // 用 C 风格字符串赋值
str = str2;                 // 用另一个 string 对象赋值
str.assign("World");        // 使用 assign 方法赋值
str.assign(5, 'b');         // 用 5 个 'b' 赋值
```

---

## **3. 访问字符**
用于访问字符串中的单个字符。

| 方法                           | 描述                                       |
| ------------------------------ | ------------------------------------------ |
| `char& operator[](size_t pos)` | 返回指定位置的字符（不检查越界）。         |
| `char& at(size_t pos)`         | 返回指定位置的字符（检查越界，抛出异常）。 |
| `char& front()`                | 返回第一个字符。                           |
| `char& back()`                 | 返回最后一个字符。                         |

**示例**：
```cpp
std::string str = "Hello";
char ch1 = str[1];          // 使用下标访问
char ch2 = str.at(1);       // 使用 at 方法访问
char ch3 = str.front();     // 访问第一个字符
char ch4 = str.back();      // 访问最后一个字符
```

---

## **4. 字符串长度**
用于获取字符串的长度或判断是否为空。

| 方法                    | 描述                                   |
| ----------------------- | -------------------------------------- |
| `size_t size() const`   | 返回字符串的长度。                     |
| `size_t length() const` | 返回字符串的长度（与 `size()` 等价）。 |
| `bool empty() const`    | 判断字符串是否为空。                   |

**示例**：
```cpp
std::string str = "Hello";
size_t len = str.size();    // 获取字符串长度
bool isEmpty = str.empty(); // 判断字符串是否为空
```

---

## **5. 字符串连接**
用于连接字符串。

| 方法                                    | 描述                                     |
| --------------------------------------- | ---------------------------------------- |
| `string& operator+=(const string& str)` | 将另一个 `string` 对象连接到当前字符串。 |
| `string& operator+=(const char* s)`     | 将 C 风格字符串连接到当前字符串。        |
| `string& operator+=(char c)`            | 将单个字符连接到当前字符串。             |
| `string& append(const string& str)`     | 将另一个 `string` 对象连接到当前字符串。 |
| `string& append(const char* s)`         | 将 C 风格字符串连接到当前字符串。        |
| `string& append(size_t n, char c)`      | 将 `n` 个字符 `c` 连接到当前字符串。     |

**示例**：
```cpp
std::string str1 = "Hello";
std::string str2 = "World";
str1 += " ";                // 使用 += 连接
str1 += str2;               // 使用 += 连接
str1.append("!");           // 使用 append 连接
```

---

## **6. 字符串比较**
用于比较两个字符串。

| 方法                                   | 描述                                   |
| -------------------------------------- | -------------------------------------- |
| `int compare(const string& str) const` | 比较当前字符串与另一个 `string` 对象。 |
| `int compare(const char* s) const`     | 比较当前字符串与 C 风格字符串。        |

**示例**：
```cpp
std::string str1 = "Hello";
std::string str2 = "World";
int result = str1.compare(str2);  // 比较字符串
if (result == 0) {
    std::cout << "Equal" << std::endl;
} else if (result < 0) {
    std::cout << "Less" << std::endl;
} else {
    std::cout << "Greater" << std::endl;
}
```

---

## **7. 子字符串**
用于提取子字符串。

| 方法                                          | 描述                                       |
| --------------------------------------------- | ------------------------------------------ |
| `string substr(size_t pos, size_t len) const` | 从 `pos` 开始提取长度为 `len` 的子字符串。 |

**示例**：
```cpp
std::string str = "Hello World";
std::string sub = str.substr(6, 5);  // 提取子字符串
// sub = "World"
```

---

## **8. 查找**
用于查找子字符串或字符。

| 方法                                                   | 描述                               |
| ------------------------------------------------------ | ---------------------------------- |
| `size_t find(const string& str, size_t pos = 0) const` | 查找子字符串，从 `pos` 开始。      |
| `size_t find(const char* s, size_t pos = 0) const`     | 查找 C 风格字符串，从 `pos` 开始。 |
| `size_t find(char c, size_t pos = 0) const`            | 查找字符，从 `pos` 开始。          |

**示例**：
```cpp
std::string str = "Hello World";
size_t pos = str.find("World");  // 查找子字符串
if (pos != std::string::npos) {
    std::cout << "Found at position: " << pos << std::endl;
}
```

---

## **9. 替换**
用于替换字符串中的部分内容。

| 方法                                                         | 描述                                       |
| ------------------------------------------------------------ | ------------------------------------------ |
| `string& replace(size_t pos, size_t len, const string& str)` | 从 `pos` 开始替换长度为 `len` 的子字符串。 |

**示例**：
```cpp
std::string str = "Hello World";
str.replace(6, 5, "C++");  // 替换子字符串
// str = "Hello C++"
```

---

## **10. 插入**
用于在字符串中插入内容。

| 方法                                            | 描述                      |
| ----------------------------------------------- | ------------------------- |
| `string& insert(size_t pos, const string& str)` | 在 `pos` 位置插入字符串。 |

**示例**：
```cpp
std::string str = "Hello World";
str.insert(5, " Beautiful");  // 插入字符串
// str = "Hello Beautiful World"
```

---

## **11. 删除**
用于删除字符串中的部分内容。

| 方法                                    | 描述                                       |
| --------------------------------------- | ------------------------------------------ |
| `string& erase(size_t pos, size_t len)` | 从 `pos` 开始删除长度为 `len` 的子字符串。 |

**示例**：
```cpp
std::string str = "Hello World";
str.erase(5, 6);  // 删除子字符串
// str = "Hello"
```

---

## **总结**
`std::string` 提供了丰富的成员函数来操作字符串，包括构造、赋值、访问、连接、比较、查找、替换、插入和删除等操作。熟练掌握这些方法可以高效地处理字符串操作。