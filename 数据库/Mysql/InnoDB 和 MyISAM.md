### **InnoDB 和 MyISAM 的详细对比**

#### **1. 事务支持**

- **InnoDB**：支持 **ACID 事务**（原子性、一致性、隔离性、持久性），适用于需要数据一致性的场景（如支付、订单系统）。
- **MyISAM**：**不支持事务**，一旦执行写操作立即生效，无法回滚，适用于读多写少的场景（如日志分析）。

#### **2. 锁机制**

- **InnoDB**：支持**行级锁**（默认）和表级锁，高并发写入时性能更优。
- **MyISAM**：仅支持**表级锁**，写入时会锁整张表，并发性能较差。

#### **3. 外键支持**

- **InnoDB**：支持**外键约束**，可维护数据完整性。
- **MyISAM**：**不支持外键**，依赖应用层维护关联逻辑。

#### **4. 索引结构**

- **InnoDB**：采用**聚簇索引**，数据与主键索引绑定，主键查询效率高，但辅助索引需二次查询。
- **MyISAM**：采用**非聚簇索引**，索引与数据分离，`COUNT(*)` 操作极快（缓存行数）。

#### **5. 崩溃恢复**

- **InnoDB**：通过 **redo log** 和 **undo log** 实现崩溃恢复，数据安全性高。
- **MyISAM**：无崩溃恢复机制，损坏后需手动修复（`REPAIR TABLE`）。

#### **6. 并发控制（MVCC）**

- **InnoDB**：支持 **MVCC（多版本并发控制）**，读写操作可并发执行，提高吞吐量。
- **MyISAM**：不支持 MVCC，高并发时易产生锁竞争。

#### **7. 存储结构**

- **InnoDB**：数据存储在**表空间**（`.ibd` 文件），支持压缩和动态行格式。
- **MyISAM**：数据分为三个文件（`.frm` 表定义、`.MYD` 数据、`.MYI` 索引）。

#### **8. 适用场景**

| **场景**                 | **推荐引擎** | **原因**                                                     |
| ------------------------ | ------------ | ------------------------------------------------------------ |
| 高并发写入、强一致性需求 | InnoDB       | 支持事务、行锁、外键，保证数据完整性。                       |
| 读多写少、无事务需求     | MyISAM       | `COUNT(*)` 快、全文索引（旧版本优势），但现代 MySQL 已默认 InnoDB。 |

#### **9. 性能差异**

- **读性能**：MyISAM 更快（无事务和行锁开销）。
- **写性能**：InnoDB 并发写入更优（行级锁 + MVCC）。
- **全文索引**：MyISAM 原生支持，InnoDB 5.6+ 才支持。

#### **10. 默认选择**

- **MySQL 5.5+** 默认使用 InnoDB，因其功能完备且稳定。
- MyISAM 仅适用于历史遗留系统或纯读负载。

### **总结**

- **InnoDB**：适合事务性、高并发、数据一致性要求高的场景（如电商、金融）。
- **MyISAM**：适合读密集型、无事务需求的场景（如日志分析），但已逐渐被淘汰。