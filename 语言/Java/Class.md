在 Java 中，`Class` 类是一个非常重要的类，用于表示类的元数据（如类名、方法、字段等）。每个类在 JVM 中都有一个对应的 `Class` 对象。以下是 `Class` 类的主要方法和属性的汇总：

---

### **1. `Class` 类的主要属性**

`Class` 类本身没有公开的属性（字段），它的属性是通过方法暴露的。

---

### **2. `Class` 类的主要方法**

#### **(1) 获取类信息**
| 方法名                       | 作用描述                                                     |
| ---------------------------- | ------------------------------------------------------------ |
| `String getName()`           | 返回类的全限定名（包括包名）。                               |
| `String getSimpleName()`     | 返回类的简单名称（不包括包名）。                             |
| `String getCanonicalName()`  | 返回类的规范名称（全限定名）。                               |
| `Package getPackage()`       | 返回类所在的包。                                             |
| `Class<?> getSuperclass()`   | 返回类的父类（超类）。                                       |
| `Class<?>[] getInterfaces()` | 返回类实现的所有接口。                                       |
| `int getModifiers()`         | 返回类的修饰符（如 `public`、`final` 等），使用 `Modifier` 类解析。 |

#### **(2) 创建实例**
| 方法名                                                       | 作用描述                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `T newInstance()`                                            | 创建类的实例（已弃用，推荐使用 `getDeclaredConstructor().newInstance()`）。 |
| `Constructor<T> getConstructor(Class<?>... parameterTypes)`  | 获取指定参数类型的公共构造方法。                             |
| `Constructor<?>[] getConstructors()`                         | 获取所有公共构造方法。                                       |
| `Constructor<T> getDeclaredConstructor(Class<?>... parameterTypes)` | 获取指定参数类型的构造方法（包括非公共的）。                 |
| `Constructor<?>[] getDeclaredConstructors()`                 | 获取所有构造方法（包括非公共的）。                           |

#### **(3) 获取字段**
| 方法名                                | 作用描述                             |
| ------------------------------------- | ------------------------------------ |
| `Field getField(String name)`         | 获取指定名称的公共字段。             |
| `Field[] getFields()`                 | 获取所有公共字段。                   |
| `Field getDeclaredField(String name)` | 获取指定名称的字段（包括非公共的）。 |
| `Field[] getDeclaredFields()`         | 获取所有字段（包括非公共的）。       |

#### **(4) 获取方法**
| 方法名                                                       | 作用描述                                       |
| ------------------------------------------------------------ | ---------------------------------------------- |
| `Method getMethod(String name, Class<?>... parameterTypes)`  | 获取指定名称和参数类型的公共方法。             |
| `Method[] getMethods()`                                      | 获取所有公共方法（包括从父类继承的）。         |
| `Method getDeclaredMethod(String name, Class<?>... parameterTypes)` | 获取指定名称和参数类型的方法（包括非公共的）。 |
| `Method[] getDeclaredMethods()`                              | 获取所有方法（包括非公共的，但不包括继承的）。 |

#### **(5) 获取注解**
| 方法名                                                       | 作用描述                     |
| ------------------------------------------------------------ | ---------------------------- |
| `<A extends Annotation> A getAnnotation(Class<A> annotationClass)` | 获取指定类型的注解。         |
| `Annotation[] getAnnotations()`                              | 获取所有注解。               |
| `<A extends Annotation> A[] getAnnotationsByType(Class<A> annotationClass)` | 获取指定类型的注解数组。     |
| `<A extends Annotation> A getDeclaredAnnotation(Class<A> annotationClass)` | 获取直接声明的指定类型注解。 |
| `Annotation[] getDeclaredAnnotations()`                      | 获取直接声明的所有注解。     |

#### **(6) 其他方法**
| 方法名                                   | 作用描述                                                  |
| ---------------------------------------- | --------------------------------------------------------- |
| `boolean isArray()`                      | 检查类是否是数组类型。                                    |
| `boolean isPrimitive()`                  | 检查类是否是基本类型（如 `int`、`boolean`）。             |
| `boolean isInterface()`                  | 检查类是否是接口。                                        |
| `boolean isEnum()`                       | 检查类是否是枚举类型。                                    |
| `boolean isAnnotation()`                 | 检查类是否是注解类型。                                    |
| `boolean isAssignableFrom(Class<?> cls)` | 检查当前类是否是指定类的父类或接口。                      |
| `ClassLoader getClassLoader()`           | 返回类的类加载器。                                        |
| `Class<?> getComponentType()`            | 返回数组类型的组件类型（如 `int[]` 的组件类型是 `int`）。 |

---

### **3. 示例代码**

以下是一个示例，展示了如何使用 `Class` 类的方法：

```java
import java.lang.reflect.Method;
import java.util.Arrays;

public class Main {
    public static void main(String[] args) throws Exception {
        // 获取 Class 对象
        Class<?> clazz = String.class;

        // 获取类名
        System.out.println("Class name: " + clazz.getName()); // java.lang.String
        System.out.println("Simple name: " + clazz.getSimpleName()); // String

        // 获取父类
        System.out.println("Superclass: " + clazz.getSuperclass()); // java.lang.Object

        // 获取实现的接口
        System.out.println("Interfaces: " + Arrays.toString(clazz.getInterfaces())); // [java.io.Serializable, java.lang.Comparable, java.lang.CharSequence]

        // 获取公共方法
        Method[] methods = clazz.getMethods();
        System.out.println("Methods:");
        for (Method method : methods) {
            System.out.println("  " + method.getName());
        }

        // 创建实例
        String str = (String) clazz.getDeclaredConstructor(String.class).newInstance("Hello");
        System.out.println("Instance: " + str); // Hello
    }
}
```

---

### **4. 总结**

| 类别           | 方法示例                                     | 作用描述                       |
| -------------- | -------------------------------------------- | ------------------------------ |
| **类信息**     | `getName()`、`getSimpleName()`               | 获取类名。                     |
| **父类与接口** | `getSuperclass()`、`getInterfaces()`         | 获取父类和实现的接口。         |
| **字段**       | `getField()`、`getDeclaredField()`           | 获取字段。                     |
| **方法**       | `getMethod()`、`getDeclaredMethod()`         | 获取方法。                     |
| **注解**       | `getAnnotation()`、`getDeclaredAnnotation()` | 获取注解。                     |
| **实例化**     | `newInstance()`                              | 创建类的实例。                 |
| **类型检查**   | `isArray()`、`isInterface()`                 | 检查类的类型（如数组、接口）。 |

- `Class` 类是 Java 反射机制的核心，用于动态获取类的元数据。
- 通过 `Class` 类，可以获取类名、字段、方法、注解等信息，并动态创建对象或调用方法。
- 在实际开发中，`Class` 类常用于框架、工具库和动态代理等场景。