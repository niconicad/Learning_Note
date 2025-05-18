要实现商品金额排行榜，并且在金额相同时根据时间排序，可以通过设计复合score的方式来实现。以下是具体方案：

### 方案1：时间戳作为小数部分（推荐）

将score设计为`金额 + (1 - 时间戳/1e13)`，其中：

- 整数部分存储金额（确保金额是主要排序依据）
- 小数部分存储时间戳的转换值（`1 - 时间戳/1e13`保证时间早的排在前面）

python

复制

```python
import redis

r = redis.Redis()

def add_product(product_id, amount, timestamp):
    # 金额为整数部分，时间戳转换后为小数部分
    final_score = amount + (1 - timestamp / 1e13)
    r.zadd("product_ranking", {product_id: final_score})

# 示例：添加商品A（金额100，时间戳1680417299000）
add_product("A", 100, 1680417299000)
```

**原理**：

1. 金额差异会体现在整数部分，确保金额大的始终排在前面
2. 当金额相同时，`1 - timestamp/1e13`会使更早的时间戳（数值更小）产生更大的小数部分，从而实现时间升序排列

### 方案2：分段组合score（适用于多条件）

如果还需要其他排序条件，可以采用分段编码：

python

复制

```python
# 假设用10位存储金额，13位存储时间戳（倒序）
final_score = (amount * 1e13) + (1e13 - timestamp)
```

### 查询示例

python

复制

```python
# 获取前10名（金额降序，时间升序）
ranking = r.zrevrange("product_ranking", 0, 9, withscores=True)
```

### 注意事项

1. Redis的score是64位浮点数，注意不要超出精度范围
2. 时间戳建议用毫秒级，确保唯一性
3. 更新金额时需要重新计算整个score

这两种方案都能实现：

- 主要按金额降序排列
- 金额相同时，按时间升序排列（先达到该金额的排在前面）

: 通过将时间戳作为小数部分组合到score中实现二级排序
 : 直接使用时间戳作为小数部分的实现示例
 : 分段存储多条件排序值的方案参考