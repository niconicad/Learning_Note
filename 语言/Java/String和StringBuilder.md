以下是String和StringBuilder常用操作的对比表格：

### String和StringBuilder常用方法对比表

| **操作类型**   | **String方法**                                               | **StringBuilder方法**                                        | **说明**                                  |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ----------------------------------------- |
| **长度/容量**  | `length()`                                                   | `length()` `capacity()`                                      | String只有长度，StringBuilder可查询容量   |
| **获取字符**   | `charAt(int index)`                                          | `charAt(int index)`                                          | 返回指定位置字符                          |
| **拼接**       | `concat(String str)` `+操作符`                               | `append(任意类型)`                                           | StringBuilder直接修改原对象，支持链式调用 |
| **插入**       | -                                                            | `insert(int offset, 任意类型)`                               | 在指定位置插入内容                        |
| **删除**       | -                                                            | `delete(int start, int end)` `deleteCharAt(int index)`       | 删除子串或指定字符                        |
| **替换**       | `replace(char old, char new)` `replaceAll(String regex, String replacement)` | `replace(int start, int end, String str)` `setCharAt(int index, char ch)` | String支持正则替换，StringBuilder直接修改 |
| **子串**       | `substring(int start, int end)`                              | `substring(int start, int end)`                              | 返回新String对象                          |
| **查找**       | `indexOf(String str)` `lastIndexOf(String str)`              | `indexOf(String str)` `lastIndexOf(String str)`              | 查找子串位置                              |
| **大小写转换** | `toLowerCase()` `toUpperCase()`                              | -                                                            | String特有                                |
| **去空格**     | `trim()`                                                     | -                                                            | String特有                                |
| **反转**       | -                                                            | `reverse()`                                                  | StringBuilder特有                         |
| **比较**       | `equals(Object obj)` `compareTo(String str)`                 | `equals(Object obj)`（比较引用） `compareTo(StringBuilder sb)` | String比较内容，StringBuilder默认比较引用 |
| **类型转换**   | `valueOf(基本类型)`                                          | `toString()`                                                 | String可将其他类型转为字符串              |
| **分割**       | `split(String regex)`                                        | -                                                            | String特有                                |
| **匹配检查**   | `matches(String regex)` `contains(CharSequence s)`           | -                                                            | String特有                                |
| **容量管理**   | -                                                            | `ensureCapacity(int min)` `trimToSize()`                     | StringBuilder特有                         |

### 特性对比

| **特性**     | **String**                   | **StringBuilder**        |
| ------------ | ---------------------------- | ------------------------ |
| **可变性**   | 不可变（每次操作生成新对象） | 可变（直接修改原对象）   |
| **线程安全** | 安全（天然不可变）           | 不安全（单线程性能更高） |
| **性能**     | 低（频繁操作生成新对象）     | 高（避免对象创建开销）   |
| **使用场景** | 少量固定字符串               | 单线程大量字符串操作     |