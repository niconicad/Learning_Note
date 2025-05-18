好的！以下是 Java 集合框架中所有常用容器（`List`、`Set`、`Map`、`Queue`）及其方法的详尽整理，包括所有常用方法的说明和示例代码。内容尽可能覆盖所有方法，并提供实例以便理解。

---

## **1. List（列表）**

List 是有序集合，允许重复元素。

### **1.1 `ArrayList`**

- **特点**：基于动态数组实现，支持随机访问，插入和删除效率较低。
- **常用方法**：

| 方法签名                                      | 说明                                              | 示例代码                                          |
| --------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- |
| `boolean add(E e)`                            | 在列表尾部添加元素。                              | `list.add("A");`                                  |
| 💖`void add(int index, E element)`             | 在指定位置插入元素。                              | `list.add(1, "B");`                               |
| 💖`E get(int index)`                           | 获取指定位置的元素。                              | `String element = list.get(0);`                   |
| `💖E set(int index, E element)`                | 替换指定位置的元素。                              | `list.set(1, "C");`                               |
| 💖`E remove(int index)`                        | 删除指定位置的元素。                              | `list.remove(0);`                                 |
| `boolean remove(Object o)`                    | 删除指定元素（首次出现）。                        | `list.remove("A");`                               |
| 💖`int size()`                                 | 返回列表中的元素数量。                            | `int size = list.size();`                         |
| `💖boolean isEmpty()`                          | 判断列表是否为空。                                | `if (list.isEmpty()) { ... }`                     |
| 💖`void clear()`                               | 清空列表。                                        | `list.clear();`                                   |
| 💖`boolean contains(Object o)`                 | 判断列表是否包含指定元素。                        | `if (list.contains("A")) { ... }`                 |
| 💖`int indexOf(Object o)`                      | 返回指定元素首次出现的索引，未找到返回 `-1`。     | `int index = list.indexOf("A");`                  |
| `int lastIndexOf(Object o)`                   | 返回指定元素最后一次出现的索引，未找到返回 `-1`。 | `int index = list.lastIndexOf("A");`              |
| `List<E> subList(int fromIndex, int toIndex)` | 返回从 `fromIndex` 到 `toIndex` 的子列表。        | `List<String> subList = list.subList(1, 3);`      |
| `Object[] toArray()`                          | 将列表转换为数组。                                | `Object[] array = list.toArray();`                |
| 💖`<T> T[] toArray(T[] a)`                     | 将列表转换为指定类型的数组。                      | `String[] array = list.toArray(new String[0]);`   |
| `Iterator<E> iterator()`                      | 返回列表的迭代器。                                | `Iterator<String> it = list.iterator();`          |
| `ListIterator<E> listIterator()`              | 返回列表的列表迭代器（支持双向遍历）。            | `ListIterator<String> it = list.listIterator();`  |
| `ListIterator<E> listIterator(int index)`     | 从指定位置返回列表迭代器。                        | `ListIterator<String> it = list.listIterator(1);` |
| `void ensureCapacity(int minCapacity)`        | 确保列表的最小容量。                              | `((ArrayList<String>) list).ensureCapacity(100);` |
| `void trimToSize()`                           | 将列表的容量调整为当前元素数量。                  | `((ArrayList<String>) list).trimToSize();`        |

---

### **1.2 `LinkedList`**

- **特点**：基于双向链表实现，插入和删除效率高，随机访问效率低。
- **常用方法**：

| 方法签名                   | 说明                                           | 示例代码                             |
| -------------------------- | ---------------------------------------------- | ------------------------------------ |
| 💖`void addFirst(E e)`      | 在列表头部添加元素。                           | `list.addFirst("A");`                |
| 💖`void addLast(E e)`       | 在列表尾部添加元素。                           | `list.addLast("B");`                 |
| 💖`E getFirst()`            | 获取列表的第一个元素。                         | `String first = list.getFirst();`    |
| 💖`E getLast()`             | 获取列表的最后一个元素。                       | `String last = list.getLast();`      |
| 💖`E removeFirst()`         | 删除并返回列表的第一个元素。                   | `String first = list.removeFirst();` |
| 💖`E removeLast()`          | 删除并返回列表的最后一个元素。                 | `String last = list.removeLast();`   |
| 💖`boolean offer(E e)`      | 在列表尾部添加元素（队列操作）。               | `list.offer("C");`                   |
| 💖`E poll()`                | 删除并返回列表的第一个元素（队列操作）。       | `String first = list.poll();`        |
| 💖`E peek()`                | 返回列表的第一个元素（队列操作）。             | `String first = list.peek();`        |
| 💖`boolean offerFirst(E e)` | 在列表头部添加元素（双端队列操作）。           | `list.offerFirst("D");`              |
| 💖`boolean offerLast(E e)`  | 在列表尾部添加元素（双端队列操作）。           | `list.offerLast("E");`               |
| 💖`E pollFirst()`           | 删除并返回列表的第一个元素（双端队列操作）。   | `String first = list.pollFirst();`   |
| 💖`E pollLast()`            | 删除并返回列表的最后一个元素（双端队列操作）。 | `String last = list.pollLast();`     |
| 💖`E peekFirst()`           | 返回列表的第一个元素（双端队列操作）。         | `String first = list.peekFirst();`   |
| `E peekLast()`             | 返回列表的最后一个元素（双端队列操作）。       | `String last = list.peekLast();`     |
| `void push(E e)`           | 将元素推入栈（列表头部）。                     | `list.push("F");`                    |
| `E pop()`                  | 弹出栈顶元素（列表头部）。                     | `String top = list.pop();`           |

---

## **2. Set（集合）**

Set 是无序集合，不允许重复元素。

### **2.1 `HashSet`**

- **特点**：基于哈希表实现，元素无序。
- **常用方法**：

| 方法签名                                    | 说明                                     | 示例代码                                       |
| ------------------------------------------- | ---------------------------------------- | ---------------------------------------------- |
| 💖`boolean add(E e)`                         | 添加元素。                               | `set.add("A");`                                |
| 💖`boolean remove(Object o)`                 | 删除指定元素。                           | `set.remove("A");`                             |
| 💖`boolean contains(Object o)`               | 判断集合是否包含指定元素。               | `if (set.contains("A")) { ... }`               |
| 💖`int size()`                               | 返回集合中的元素数量。                   | `int size = set.size();`                       |
| `boolean isEmpty()`                         | 判断集合是否为空。                       | `if (set.isEmpty()) { ... }`                   |
| `void clear()`                              | 清空集合。                               | `set.clear();`                                 |
| `Iterator<E> iterator()`                    | 返回集合的迭代器。                       | `Iterator<String> it = set.iterator();`        |
| `Object[] toArray()`                        | 将集合转换为数组。                       | `Object[] array = set.toArray();`              |
| `<T> T[] toArray(T[] a)`                    | 将集合转换为指定类型的数组。             | `String[] array = set.toArray(new String[0]);` |
| `boolean addAll(Collection<? extends E> c)` | 将指定集合中的所有元素添加到当前集合。   | `set.addAll(anotherSet);`                      |
| `boolean removeAll(Collection<?> c)`        | 删除当前集合中与指定集合相同的元素。     | `set.removeAll(anotherSet);`                   |
| `boolean retainAll(Collection<?> c)`        | 仅保留当前集合中与指定集合相同的元素。   | `set.retainAll(anotherSet);`                   |
| `boolean containsAll(Collection<?> c)`      | 判断当前集合是否包含指定集合的所有元素。 | `if (set.containsAll(anotherSet)) { ... }`     |

---

### **2.2 `TreeSet`**

- **特点**：基于红黑树实现，元素有序。
- **常用方法**：

| 方法签名                                                     | 说明                                | 示例代码                                                     |
| ------------------------------------------------------------ | ----------------------------------- | ------------------------------------------------------------ |
| 💖`E first()`                                                 | 返回集合的第一个元素。              | `String first = set.first();`                                |
| 💖`E last()`                                                  | 返回集合的最后一个元素。            | `String last = set.last();`                                  |
| 💖`E lower(E e)`                                              | 返回小于指定元素的最大元素。        | `String lower = set.lower("B");`                             |
| `E higher(E e)`                                              | 返回大于指定元素的最小元素。        | `String higher = set.higher("B");`                           |
| `E floor(E e)`                                               | 返回小于或等于指定元素的最大元素。  | `String floor = set.floor("B");`                             |
| 💖`E ceiling(E e)`                                            | 返回大于或等于指定元素的最小元素。  | `String ceiling = set.ceiling("B");`                         |
| 💖`E pollFirst()`                                             | 删除并返回集合的第一个元素。        | `String first = set.pollFirst();`                            |
| `E pollLast()`                                               | 删除并返回集合的最后一个元素。      | `String last = set.pollLast();`                              |
| `NavigableSet<E> descendingSet()`                            | 返回集合的逆序视图。                | `NavigableSet<String> descending = set.descendingSet();`     |
| `Iterator<E> descendingIterator()`                           | 返回集合的逆序迭代器。              | `Iterator<String> it = set.descendingIterator();`            |
| `NavigableSet<E> subSet(E from, boolean fromInclusive, E to, boolean toInclusive)` | 返回从 `from` 到 `to` 的子集合。    | `NavigableSet<String> subSet = set.subSet("A", true, "C", false);` |
| `NavigableSet<E> headSet(E to, boolean inclusive)`           | 返回小于（或等于）`to` 的子集合。   | `NavigableSet<String> headSet = set.headSet("C", true);`     |
| `NavigableSet<E> tailSet(E from, boolean inclusive)`         | 返回大于（或等于）`from` 的子集合。 | `NavigableSet<String> tailSet = set.tailSet("A", true);`     |

---

## **3. Map（映射）**

Map 是键值对集合，键唯一。

### **3.1 `HashMap`**

- **特点**：基于哈希表实现，键值对无序。
- **常用方法**：

| 方法签名                                                     | 说明                                   | 示例代码                                                   |
| ------------------------------------------------------------ | -------------------------------------- | ---------------------------------------------------------- |
| `V put(K key, V value)`                                      | 添加键值对。                           | `map.put("key", "value");`                                 |
| `V get(Object key)`                                          | 获取指定键的值。                       | `String value = map.get("key");`                           |
| `V remove(Object key)`                                       | 删除指定键的键值对。                   | `map.remove("key");`                                       |
| `boolean containsKey(Object key)`                            | 判断是否包含指定键。                   | `if (map.containsKey("key")) { ... }`                      |
| `boolean containsValue(Object value)`                        | 判断是否包含指定值。                   | `if (map.containsValue("value")) { ... }`                  |
| `Set<K> keySet()`                                            | 返回所有键的集合。                     | `Set<String> keys = map.keySet();`                         |
| `Collection<V> values()`                                     | 返回所有值的集合。                     | `Collection<String> values = map.values();`                |
| 💖`Set<Map.Entry<K, V>> entrySet()`                           | 返回所有键值对的集合。                 | `Set<Map.Entry<String, String>> entries = map.entrySet();` |
| `int size()`                                                 | 返回键值对数量。                       | `int size = map.size();`                                   |
| `boolean isEmpty()`                                          | 判断是否为空。                         | `if (map.isEmpty()) { ... }`                               |
| `void clear()`                                               | 清空映射。                             | `map.clear();`                                             |
| `V getOrDefault(Object key, V defaultValue)`                 | 获取指定键的值，若不存在则返回默认值。 | `String value = map.getOrDefault("key", "default");`       |
| `V putIfAbsent(K key, V value)`                              | 若键不存在，则添加键值对。             | `map.putIfAbsent("key", "value");`                         |
| `boolean remove(Object key, Object value)`                   | 删除指定键值对。                       | `map.remove("key", "value");`                              |
| `boolean replace(K key, V oldValue, V newValue)`             | 替换指定键值对。                       | `map.replace("key", "oldValue", "newValue");`              |
| `V replace(K key, V value)`                                  | 替换指定键的值。                       | `map.replace("key", "value");`                             |
| `void forEach(BiConsumer<? super K, ? super V> action)`      | 对每个键值对执行操作。                 | `map.forEach((k, v) -> System.out.println(k + ": " + v));` |
| `void replaceAll(BiFunction<? super K, ? super V, ? extends V> function)` | 替换所有键值对的值。                   | `map.replaceAll((k, v) -> v.toUpperCase());`               |

---

### **3.2 `TreeMap`**

- **特点**：基于红黑树实现，键值对有序。
- **常用方法**：

| 方法签名                                                     | 说明                                | 示例代码                                                     |
| ------------------------------------------------------------ | ----------------------------------- | ------------------------------------------------------------ |
| `K firstKey()`                                               | 返回第一个键。                      | `String firstKey = map.firstKey();`                          |
| `K lastKey()`                                                | 返回最后一个键。                    | `String lastKey = map.lastKey();`                            |
| `Map.Entry<K, V> firstEntry()`                               | 返回第一个键值对。                  | `Map.Entry<String, String> firstEntry = map.firstEntry();`   |
| `Map.Entry<K, V> lastEntry()`                                | 返回最后一个键值对。                | `Map.Entry<String, String> lastEntry = map.lastEntry();`     |
| `Map.Entry<K, V> pollFirstEntry()`                           | 删除并返回第一个键值对。            | `Map.Entry<String, String> firstEntry = map.pollFirstEntry();` |
| `Map.Entry<K, V> pollLastEntry()`                            | 删除并返回最后一个键值对。          | `Map.Entry<String, String> lastEntry = map.pollLastEntry();` |
| `K lowerKey(K key)`                                          | 返回小于指定键的最大键。            | `String lowerKey = map.lowerKey("B");`                       |
| `K higherKey(K key)`                                         | 返回大于指定键的最小键。            | `String higherKey = map.higherKey("B");`                     |
| `K floorKey(K key)`                                          | 返回小于或等于指定键的最大键。      | `String floorKey = map.floorKey("B");`                       |
| `K ceilingKey(K key)`                                        | 返回大于或等于指定键的最小键。      | `String ceilingKey = map.ceilingKey("B");`                   |
| `NavigableMap<K, V> descendingMap()`                         | 返回映射的逆序视图。                | `NavigableMap<String, String> descending = map.descendingMap();` |
| `NavigableSet<K> descendingKeySet()`                         | 返回键的逆序集合。                  | `NavigableSet<String> descendingKeys = map.descendingKeySet();` |
| `NavigableMap<K, V> subMap(K from, boolean fromInclusive, K to, boolean toInclusive)` | 返回从 `from` 到 `to` 的子映射。    | `NavigableMap<String, String> subMap = map.subMap("A", true, "C", false);` |
| `NavigableMap<K, V> headMap(K to, boolean inclusive)`        | 返回小于（或等于）`to` 的子映射。   | `NavigableMap<String, String> headMap = map.headMap("C", true);` |
| `NavigableMap<K, V> tailMap(K from, boolean inclusive)`      | 返回大于（或等于）`from` 的子映射。 | `NavigableMap<String, String> tailMap = map.tailMap("A", true);` |

---

## **4. Queue（队列）**

Queue 是先进先出（FIFO）的集合。

### **4.1 `LinkedList`（作为队列使用）**

- **常用方法**：

| 方法签名             | 说明                                   | 示例代码                         |
| -------------------- | -------------------------------------- | -------------------------------- |
| `boolean offer(E e)` | 在队列尾部添加元素。                   | `queue.offer("A");`              |
| `E poll()`           | 删除并返回队列头部的元素。             | `String head = queue.poll();`    |
| `E peek()`           | 返回队列头部的元素。                   | `String head = queue.peek();`    |
| `boolean add(E e)`   | 在队列尾部添加元素（队列操作）。       | `queue.add("B");`                |
| `E remove()`         | 删除并返回队列头部的元素（队列操作）。 | `String head = queue.remove();`  |
| `E element()`        | 返回队列头部的元素（队列操作）。       | `String head = queue.element();` |

---

### **4.2 `PriorityQueue`**

- **常用方法**：

| 方法签名                             | 说明                         | 示例代码                                         |
| ------------------------------------ | ---------------------------- | ------------------------------------------------ |
| `boolean offer(E e)`                 | 添加元素。                   | `queue.offer("A");`                              |
| `E poll()`                           | 删除并返回优先级最高的元素。 | `String head = queue.poll();`                    |
| `E peek()`                           | 返回优先级最高的元素。       | `String head = queue.peek();`                    |
| `boolean add(E e)`                   | 添加元素。                   | `queue.add("B");`                                |
| `E remove()`                         | 删除并返回优先级最高的元素。 | `String head = queue.remove();`                  |
| `E element()`                        | 返回优先级最高的元素。       | `String head = queue.element();`                 |
| `Comparator<? super E> comparator()` | 返回队列的比较器。           | `Comparator<String> comp = queue.comparator();`  |
| `void clear()`                       | 清空队列。                   | `queue.clear();`                                 |
| `boolean contains(Object o)`         | 判断队列是否包含指定元素。   | `if (queue.contains("A")) { ... }`               |
| `Iterator<E> iterator()`             | 返回队列的迭代器。           | `Iterator<String> it = queue.iterator();`        |
| `int size()`                         | 返回队列中的元素数量。       | `int size = queue.size();`                       |
| `Object[] toArray()`                 | 将队列转换为数组。           | `Object[] array = queue.toArray();`              |
| `<T> T[] toArray(T[] a)`             | 将队列转换为指定类型的数组。 | `String[] array = queue.toArray(new String[0]);` |

---

## **5. 工具类**

### **5.1 `Collections`**

| 方法签名                                                 | 说明                             | 示例代码                                                     |
| -------------------------------------------------------- | -------------------------------- | ------------------------------------------------------------ |
| 💖`void sort(List<T> list)`                               | 对列表排序。                     | `Collections.sort(list);`                                    |
| 💖`void reverse(List<?> list)`                            | 反转列表。                       | `Collections.reverse(list);`                                 |
| `void shuffle(List<?> list)`                             | 随机打乱列表。                   | `Collections.shuffle(list);`                                 |
| 💖`T max(Collection<? extends T> coll)`                   | 返回集合中的最大值。             | `String max = Collections.max(list);`                        |
| `T min(Collection<? extends T> coll)`                    | 返回集合中的最小值。             | `String min = Collections.min(list);`                        |
| `void copy(List<? super T> dest, List<? extends T> src)` | 将源列表复制到目标列表。         | `Collections.copy(dest, src);`                               |
| `void fill(List<? super T> list, T obj)`                 | 用指定元素填充列表。             | `Collections.fill(list, "A");`                               |
| `int frequency(Collection<?> c, Object o)`               | 返回指定元素在集合中出现的次数。 | `int count = Collections.frequency(list, "A");`              |
| `boolean disjoint(Collection<?> c1, Collection<?> c2)`   | 判断两个集合是否没有交集。       | `if (Collections.disjoint(set1, set2)) { ... }`              |
| `List<T> synchronizedList(List<T> list)`                 | 返回线程安全的列表。             | `List<String> syncList = Collections.synchronizedList(list);` |
| `Set<T> synchronizedSet(Set<T> s)`                       | 返回线程安全的集合。             | `Set<String> syncSet = Collections.synchronizedSet(set);`    |
| `Map<K, V> synchronizedMap(Map<K, V> m)`                 | 返回线程安全的映射。             | `Map<String, String> syncMap = Collections.synchronizedMap(map);` |

---

### **5.2 `Arrays`**

| 方法签名                                                     | 说明                             | 示例代码                                               |
| ------------------------------------------------------------ | -------------------------------- | ------------------------------------------------------ |
| 💖`void sort(T[] a)`                                          | 对数组排序。                     | `Arrays.sort(array);`                                  |
| `int binarySearch(T[] a, T key)`                             | 二分查找。                       | `int index = Arrays.binarySearch(array, "A");`         |
| `List<T> asList(T... a)`                                     | 将数组转换为列表。               | `List<String> list = Arrays.asList("A", "B", "C");`    |
| `String toString(T[] a)`                                     | 将数组转换为字符串。             | `String str = Arrays.toString(array);`                 |
| `void fill(T[] a, T val)`                                    | 用指定值填充数组。               | `Arrays.fill(array, "A");`                             |
| `boolean equals(T[] a, T[] a2)`                              | 判断两个数组是否相等。           | `if (Arrays.equals(array1, array2)) { ... }`           |
| `T[] copyOf(T[] original, int newLength)`                    | 复制数组，指定新长度。           | `String[] newArray = Arrays.copyOf(array, 10);`        |
| `T[] copyOfRange(T[] original, int from, int to)`            | 复制数组的指定范围。             | `String[] newArray = Arrays.copyOfRange(array, 1, 3);` |
| `int hashCode(T[] a)`                                        | 返回数组的哈希值。               | `int hash = Arrays.hashCode(array);`                   |
| `void parallelSort(T[] a)`                                   | 并行排序数组（Java 8+）。        | `Arrays.parallelSort(array);`                          |
| `void setAll(T[] array, IntFunction<? extends T> generator)` | 使用生成函数设置数组的所有元素。 | `Arrays.setAll(array, i -> "A" + i);`                  |
| `void parallelSetAll(T[] array, IntFunction<? extends T> generator)` | 并行设置数组的所有元素。         | `Arrays.parallelSetAll(array, i -> "A" + i);`          |

---

### **总结**
以上整理了 Java 集合框架中所有常用容器及其方法，并提供了详细的示例代码。根据具体需求选择合适的容器和方法，可以显著提高代码的效率和可读性。