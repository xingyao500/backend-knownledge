## 操作
### 复制已有数据到新表

table1:

|c1|c2|c3|c4|c5
|----|----|----|----|-----|
|v1|v2|v3|v4|v5|

table2:

|c1|c2|c3|
|-----|-----|-----|
|v1|v2|v3|

```sql
# 只复制 table2 中的数据
insert into [table1]
(c1, c2, c3)
select c1,c2,c3
from [table2]
where ....

# 复制包含不存在 table2 的数据
insert into [table1]
(c1, c2, c3, c4, c5)
select c1,c2,c3, [取值1], [取值2]
from [table2]
where ....
```

## 性能

### 查询记得限定 `limit`