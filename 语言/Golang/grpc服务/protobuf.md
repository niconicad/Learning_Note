在Go语言的Web开发中，常用的库和框架可以显著提升开发效率和性能。以下是核心库及其用法分类说明：

------

### **1. 标准库**

#### **(1) `net/http`**

- **功能**：构建HTTP服务器/客户端，处理请求和响应。

- 

  示例

  ：

  go

  go

  复制

  ```go
  package main
  import (
      "fmt"
      "net/http"
  )
  func handler(w http.ResponseWriter, r *http.Request) {
      fmt.Fprintf(w, "Hello, World!")
  }
  func main() {
      http.HandleFunc("/", handler)
      http.ListenAndServe(":8080", nil)
  }
  ```

- **适用场景**：简单HTTP服务或学习用途。

#### **(2) `encoding/json`**

- **功能**：JSON数据的序列化与反序列化。

- 

  示例

  ：

  go

  go

  复制

  ```go
  type User struct { Name string `json:"name"` }
  data, _ := json.Marshal(User{Name: "Alice"})
  ```

- **适用场景**：API开发中的数据传输。

------

### **2. Web框架**

#### **(1) Gin**

- **特点**：高性能、轻量级，支持中间件和路由分组。

- 

  示例

  ：

  go

  go

  复制

  ```go
  package main
  import "github.com/gin-gonic/gin"
  func main() {
      r := gin.Default()
      r.GET("/ping", func(c *gin.Context) {
          c.JSON(200, gin.H{"message": "pong"})
      })
      r.Run()
  }
  ```

- **适用场景**：RESTful API、微服务。

#### **(2) Echo**

- **特点**：简洁API、高性能，内置日志和错误处理。

- 

  示例

  ：

  go

  go

  复制

  ```go
  e := echo.New()
  e.GET("/", func(c echo.Context) error {
      return c.String(200, "Hello, Echo!")
  })
  ```

- **适用场景**：快速开发Web应用。

#### **(3) Beego**

- **特点**：全栈框架，内置ORM、缓存、日志等模块。

- 

  示例

  ：

  go

  go

  复制

  ```go
  beego.Run()  // 默认监听8080端口
  ```

- **适用场景**：企业级应用。

------

### **3. 数据库操作**

#### **(1) GORM**

- **功能**：ORM库，支持MySQL/PostgreSQL等。

- 

  示例

  ：

  go

  go

  复制

  ```go
  db, _ := gorm.Open(sqlite.Open("test.db"), &gorm.Config{})
  db.AutoMigrate(&User{})
  db.Create(&User{Name: "John"})
  ```

- **适用场景**：简化数据库CRUD操作。

#### **(2) `database/sql`**

- **功能**：标准库接口，需配合驱动（如`go-sql-driver/mysql`）。

- 

  示例

  ：

  go

  go

  复制

  ```go
  db, _ := sql.Open("mysql", "user:pass@/dbname")
  rows, _ := db.Query("SELECT * FROM users")
  ```

- **适用场景**：原生SQL操作。

------

### **4. 模板引擎**

#### **(1) `html/template`**

- **功能**：动态生成HTML，防XSS攻击。

- 

  示例

  ：

  go

  go

  复制

  ```go
  tmpl := template.Must(template.ParseFiles("index.html"))
  tmpl.Execute(w, data)
  ```

- **适用场景**：服务端渲染（SSR）。

------

### **5. 其他实用库**

| 库名       | 功能                  | 示例场景               |
| ---------- | --------------------- | ---------------------- |
| **Viper**  | 配置管理（YAML/JSON） | 读取环境变量和配置文件 |
| **Zap**    | 高性能日志记录        | 替代标准库`log`        |
| **JWT-go** | 生成/验证JWT令牌      | 用户认证               |

------

### **选择建议**

- **性能优先**：Gin或Fiber。
- **全栈开发**：Beego或Revel。
- **轻量级**：Echo或标准库`net/http`。

通过合理选择库和框架，可以高效构建安全、高性能的Go Web应用。