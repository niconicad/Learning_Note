Java 提供了丰富的数组操作库函数，主要通过 `java.util.Arrays` 类和 `java.lang.System` 类来实现。以下是常用的数组库函数及其用法：

---

### **1. 数组排序**
#### **`Arrays.sort()`**
- 对数组进行排序（升序）。
- 支持基本类型数组和对象数组。
- 示例：
  ```java
  import java.util.Arrays;
  
  int[] arr = {5, 3, 1, 4, 2};
  Arrays.sort(arr); // 排序后 arr = [1, 2, 3, 4, 5]
  ```

#### **自定义排序**
- 使用 `Comparator` 对对象数组进行自定义排序。
- 示例：
  ```java
  import java.util.Arrays;
  import java.util.Comparator;
  
  String[] arr = {"banana", "apple", "cherry"};
  Arrays.sort(arr, Comparator.reverseOrder()); // 降序排序
  ```

---

### **2. 数组查找**
#### **`Arrays.binarySearch()`**
- 对已排序的数组进行二分查找。
- 返回元素的索引（如果找到），否则返回负数。
- 示例：
  ```java
  import java.util.Arrays;
  
  int[] arr = {1, 2, 3, 4, 5};
  int index = Arrays.binarySearch(arr, 3); // index = 2
  ```

---

### **3. 数组填充**
#### **`Arrays.fill()`**
- 将数组的所有元素填充为指定值。
- 示例：
  ```java
  import java.util.Arrays;
  
  int[] arr = new int[5];
  Arrays.fill(arr, 10); // arr = [10, 10, 10, 10, 10]
  ```

---

### **4. 数组复制**
#### **`Arrays.copyOf()`**
- 复制数组的一部分或全部。
- 示例：
  ```java
  import java.util.Arrays;
  
  int[] arr = {1, 2, 3, 4, 5};
  int[] copy = Arrays.copyOf(arr, 3); // copy = [1, 2, 3]
  ```

#### **`Arrays.copyOfRange()`**
- 复制数组的指定范围。
- 示例：
  ```java
  import java.util.Arrays;
  
  int[] arr = {1, 2, 3, 4, 5};
  int[] copy = Arrays.copyOfRange(arr, 1, 4); // copy = [2, 3, 4]
  ```

#### **`System.arraycopy()`**
- 高效地复制数组的一部分。
- 示例：
  ```java
  int[] src = {1, 2, 3, 4, 5};
  int[] dest = new int[3];
  System.arraycopy(src, 1, dest, 0, 3); // dest = [2, 3, 4]
  ```

---

### **5. 数组比较**
#### **`Arrays.equals()`**
- 比较两个数组是否相等（元素顺序和值相同）。
- 示例：
  ```java
  import java.util.Arrays;
  
  int[] arr1 = {1, 2, 3};
  int[] arr2 = {1, 2, 3};
  boolean isEqual = Arrays.equals(arr1, arr2); // isEqual = true
  ```

#### **`Arrays.deepEquals()`**
- 比较多维数组是否相等。
- 示例：
  ```java
  import java.util.Arrays;
  
  int[][] arr1 = {{1, 2}, {3, 4}};
  int[][] arr2 = {{1, 2}, {3, 4}};
  boolean isEqual = Arrays.deepEquals(arr1, arr2); // isEqual = true
  ```

---

### **6. 数组转字符串**
#### **`Arrays.toString()`**
- 将数组转换为字符串表示。
- 示例：
  ```java
  import java.util.Arrays;
  
  int[] arr = {1, 2, 3};
  String str = Arrays.toString(arr); // str = "[1, 2, 3]"
  ```

#### **`Arrays.deepToString()`**
- 将多维数组转换为字符串表示。
- 示例：
  ```java
  import java.util.Arrays;
  
  int[][] arr = {{1, 2}, {3, 4}};
  String str = Arrays.deepToString(arr); // str = "[[1, 2], [3, 4]]"
  ```

---

### **7. 数组转换为列表**
#### **`Arrays.asList()`**
- 将数组转换为 `List`。
- 示例：
  ```java
  import java.util.Arrays;
  import java.util.List;
  
  String[] arr = {"apple", "banana", "cherry"};
  List<String> list = Arrays.asList(arr); // list = [apple, banana, cherry]
  ```

---

### **8. 数组流操作**
#### **`Arrays.stream()`**
- 将数组转换为流（`Stream`），支持函数式操作。
- 示例：
  ```java
  import java.util.Arrays;
  
  int[] arr = {1, 2, 3, 4, 5};
  int sum = Arrays.stream(arr).sum(); // sum = 15
  ```

---

### **9. 数组填充默认值**
#### **`Arrays.setAll()`**
- 使用生成函数填充数组。
- 示例：
  ```java
  import java.util.Arrays;
  
  int[] arr = new int[5];
  Arrays.setAll(arr, i -> i * 2); // arr = [0, 2, 4, 6, 8]
  ```

---

### **10. 数组并行操作**
#### **`Arrays.parallelSort()`**
- 对数组进行并行排序。
- 示例：
  ```java
  import java.util.Arrays;
  
  int[] arr = {5, 3, 1, 4, 2};
  Arrays.parallelSort(arr); // arr = [1, 2, 3, 4, 5]
  ```

#### **`Arrays.parallelPrefix()`**
- 对数组进行并行前缀计算。
- 示例：
  ```java
  import java.util.Arrays;
  
  int[] arr = {1, 2, 3, 4, 5};
  Arrays.parallelPrefix(arr, (a, b) -> a + b); // arr = [1, 3, 6, 10, 15]
  ```

---

### **总结**
Java 提供了丰富的数组操作库函数，涵盖了排序、查找、复制、比较、转换等常见操作。通过合理使用这些函数，可以简化代码并提高开发效率。以下是常用函数的快速参考：

| 功能         | 方法                      | 示例                                          |
| ------------ | ------------------------- | --------------------------------------------- |
| 排序         | `Arrays.sort()`           | `Arrays.sort(arr)`                            |
| 查找         | `Arrays.binarySearch()`   | `Arrays.binarySearch(arr, key)`               |
| 填充         | `Arrays.fill()`           | `Arrays.fill(arr, value)`                     |
| 复制         | `Arrays.copyOf()`         | `Arrays.copyOf(arr, length)`                  |
| 比较         | `Arrays.equals()`         | `Arrays.equals(arr1, arr2)`                   |
| 转字符串     | `Arrays.toString()`       | `Arrays.toString(arr)`                        |
| 转换为列表   | `Arrays.asList()`         | `Arrays.asList(arr)`                          |
| 流操作       | `Arrays.stream()`         | `Arrays.stream(arr).sum()`                    |
| 并行排序     | `Arrays.parallelSort()`   | `Arrays.parallelSort(arr)`                    |
| 并行前缀计算 | `Arrays.parallelPrefix()` | `Arrays.parallelPrefix(arr, (a, b) -> a + b)` |