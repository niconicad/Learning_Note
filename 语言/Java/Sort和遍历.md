# Java 容器与数组排序方法及 HashMap/HashSet 遍历方式总结

## 一、数组排序

### 1. 基本类型数组排序

java

复制

```java
int[] arr = {5, 2, 9, 1, 5};
Arrays.sort(arr); // 升序排序
Arrays.sort(arr, 1, 4); // 对索引1到3(不包括4)的元素排序
```

### 2. 对象数组排序

java

复制

```java
String[] strArr = {"banana", "apple", "pear"};
Arrays.sort(strArr); // 按自然顺序排序

// 自定义排序
Arrays.sort(strArr, (a, b) -> b.compareTo(a)); // 降序排序
Arrays.sort(strArr, Comparator.comparing(String::length)); // 按字符串长度排序
```

## 二、List 排序

### 1. Collections.sort()

java

复制

```java
List<Integer> list = new ArrayList<>(Arrays.asList(5, 2, 9, 1, 5));
Collections.sort(list); // 升序排序

// 自定义排序
Collections.sort(list, (a, b) -> b - a); // 降序排序
Collections.sort(list, Comparator.reverseOrder()); // 降序排序
```

### 2. List.sort() (Java 8+)

java

复制

```java
list.sort(Comparator.naturalOrder()); // 升序排序
list.sort(Comparator.comparingInt(String::length)); // 按字符串长度排序
```

## 三、Set 排序

### 1. TreeSet (自动排序)

java

复制

```java
Set<Integer> sortedSet = new TreeSet<>(list); // 自动升序排序
Set<Integer> descSet = new TreeSet<>(Comparator.reverseOrder());
descSet.addAll(list); // 降序排序
```

### 2. 转换为List后排序

java

复制

```java
Set<String> set = new HashSet<>(Arrays.asList("banana", "apple", "pear"));
List<String> sortedList = new ArrayList<>(set);
sortedList.sort(String::compareToIgnoreCase); // 不区分大小写排序
```

## 四、Map 排序

### 1. 按Key排序

java

复制

```java
Map<String, Integer> map = new HashMap<>();
// 填充map...

// 转换为TreeMap自动按键排序
Map<String, Integer> sortedByKey = new TreeMap<>(map);

// 自定义Key排序
Map<String, Integer> customSorted = new TreeMap<>(
    Comparator.comparingInt(String::length).thenComparing(Comparator.naturalOrder())
);
customSorted.putAll(map);
```

### 2. 按Value排序

java

复制

```java
// 转换为List<Entry>后排序
List<Map.Entry<String, Integer>> entryList = new ArrayList<>(map.entrySet());
entryList.sort(Map.Entry.comparingByValue()); // 按value升序
entryList.sort(Map.Entry.comparingByValue(Comparator.reverseOrder())); // 降序

// Java 8 Stream方式
Map<String, Integer> sortedByValue = map.entrySet().stream()
    .sorted(Map.Entry.comparingByValue())
    .collect(Collectors.toMap(
        Map.Entry::getKey,
        Map.Entry::getValue,
        (e1, e2) -> e1,
        LinkedHashMap::new // 保持排序结果
    ));
```

## 五、HashMap 遍历方式

### 1. 使用EntrySet (推荐)

java

复制

```java
for (Map.Entry<String, Integer> entry : map.entrySet()) {
    System.out.println("Key: " + entry.getKey() + ", Value: " + entry.getValue());
}
```

### 2. 使用KeySet

java

复制

```java
for (String key : map.keySet()) {
    System.out.println("Key: " + key + ", Value: " + map.get(key));
}
```

### 3. 使用values()

java

复制

```java
for (Integer value : map.values()) {
    System.out.println("Value: " + value);
}
```

### 4. Java 8 forEach

java

复制

```java
map.forEach((k, v) -> System.out.println("Key: " + k + ", Value: " + v));
```

## 六、HashSet 遍历方式

### 1. 增强for循环

java

复制

```java
for (String item : set) {
    System.out.println(item);
}
```

### 2. 使用Iterator

java

复制

```java
Iterator<String> it = set.iterator();
while (it.hasNext()) {
    System.out.println(it.next());
}
```

### 3. Java 8 forEach

java

复制

```java
set.forEach(System.out::println);
```

### 4. Stream API

java

复制

```java
set.stream().forEach(System.out::println);
```

## 七、性能比较

| 操作               | 时间复杂度         | 适用场景           |
| ------------------ | ------------------ | ------------------ |
| 数组排序           | O(n log n)         | 基本类型和对象数组 |
| Collections.sort() | O(n log n)         | List接口实现类     |
| TreeSet/TreeMap    | O(log n) 插入/查找 | 需要自动排序的集合 |
| HashMap遍历        | O(n)               | 需要访问所有元素   |
| HashSet遍历        | O(n)               | 需要访问所有元素   |

## 八、最佳实践建议

1. **排序选择**：
   - 基本类型数组优先使用 `Arrays.sort()`
   - List集合优先使用 `list.sort()` (Java 8+)
   - 需要自动排序的集合使用 `TreeSet`/`TreeMap`
2. **遍历选择**：
   - HashMap遍历推荐使用 `entrySet()`，避免多次查找
   - 只需要keys或values时使用对应的 `keySet()` 或 `values()`
   - Java 8+ 环境下可以使用简洁的 `forEach` 语法
3. **线程安全**：
   - 多线程环境下考虑使用 `Collections.synchronizedXXX()` 包装
   - 或使用 `ConcurrentHashMap`/`CopyOnWriteArraySet`