# 飞书多维表格结构参考

## 创建顺序

1. 创建 App（`feishu_bitable_app` action=create）
2. 依次创建 4 张数据表（`feishu_bitable_app_table` action=create，在 create 时传入 fields）
3. 将 app_token 和各 table_id 写入用户档案

---

## 表 1：训练记录（总览）

表名：`训练记录`

| 字段名 | 类型 | type值 | 备注 |
|--------|------|--------|------|
| 日期 | 日期 | 5 | 必填 |
| 训练类型 | 单选 | 3 | 选项：胸日、背日、肩日、腿日、全身、有氧、休息 |
| 训练状态 | 单选 | 3 | 选项：待完成、已完成、已跳过；预排时填「待完成」，打卡后更新 |
| 训练时长（分钟） | 数字 | 2 | 用户未提供时按 60 分钟估算 |
| 消耗热量（kcal） | 数字 | 2 | 有设备填设备数据；无设备按公式估算（见 SKILL.md 流程二） |
| 消耗来源 | 单选 | 3 | 选项：设备数据、公式估算；区分数据可信度 |
| 备注 | 文本 | 1 | 估算时注明，如「无设备，MET=3.5×60min×72kg/60」 |

创建示例：
```json
{
  "name": "训练记录",
  "fields": [
    {"field_name": "日期", "type": 5},
    {"field_name": "训练类型", "type": 3, "property": {"options": [
      {"name": "胸日"}, {"name": "背日"}, {"name": "肩日"},
      {"name": "腿日"}, {"name": "全身"}, {"name": "有氧"}, {"name": "休息"}
    ]}},
    {"field_name": "训练状态", "type": 3, "property": {"options": [
      {"name": "待完成"}, {"name": "已完成"}, {"name": "已跳过"}
    ]}},
    {"field_name": "训练时长（分钟）", "type": 2},
    {"field_name": "消耗热量（kcal）", "type": 2},
    {"field_name": "消耗来源", "type": 3, "property": {"options": [
      {"name": "设备数据"}, {"name": "公式估算"}
    ]}},
    {"field_name": "备注", "type": 1}
  ]
}
```

---

## 表 2：动作明细

表名：`动作明细`

| 字段名 | 类型 | type值 | 备注 |
|--------|------|--------|------|
| 日期 | 日期 | 5 | 必填 |
| 动作名称 | 文本 | 1 | 必填 |
| 组数 | 数字 | 2 | |
| 次数 | 数字 | 2 | |
| 重量（kg） | 数字 | 2 | 自重动作填0 |
| 备注 | 文本 | 1 | |

创建示例：
```json
{
  "name": "动作明细",
  "fields": [
    {"field_name": "日期", "type": 5},
    {"field_name": "动作名称", "type": 1},
    {"field_name": "组数", "type": 2},
    {"field_name": "次数", "type": 2},
    {"field_name": "重量（kg）", "type": 2},
    {"field_name": "备注", "type": 1}
  ]
}
```

---

## 表 3：饮食记录

表名：`饮食记录`

| 字段名 | 类型 | type值 | 备注 |
|--------|------|--------|------|
| 日期 | 日期 | 5 | 必填 |
| 碳日类型 | 单选 | 3 | 高碳日/中碳日/低碳日（初始化时预填，方案A/C留空） |
| 碳水目标（g） | 数字 | 2 | 根据碳日类型自动填入 |
| 热量目标（kcal） | 数字 | 2 | 根据碳日类型自动填入 |
| 餐次 | 单选 | 3 | 选项：早餐、午餐、晚餐、加餐 |
| 食物描述 | 文本 | 1 | 如"鸡胸肉200g + 米饭150g" |
| 热量（kcal） | 数字 | 2 | 实际摄入 |
| 蛋白质（g） | 数字 | 2 | |
| 碳水（g） | 数字 | 2 | |
| 脂肪（g） | 数字 | 2 | |

创建示例：
```json
{
  "name": "饮食记录",
  "fields": [
    {"field_name": "日期", "type": 5},
    {"field_name": "碳日类型", "type": 3, "property": {"options": [
      {"name": "高碳日"}, {"name": "中碳日"}, {"name": "低碳日"},
      {"name": "极高碳日"}, {"name": "极低碳日"}
    ]}},
    {"field_name": "碳水目标（g）", "type": 2},
    {"field_name": "热量目标（kcal）", "type": 2},
    {"field_name": "餐次", "type": 3, "property": {"options": [
      {"name": "早餐"}, {"name": "午餐"}, {"name": "晚餐"}, {"name": "加餐"}
    ]}},
    {"field_name": "食物描述", "type": 1},
    {"field_name": "热量（kcal）", "type": 2},
    {"field_name": "蛋白质（g）", "type": 2},
    {"field_name": "碳水（g）", "type": 2},
    {"field_name": "脂肪（g）", "type": 2}
  ]
}
```

---

## 表 4：体重体脂记录

表名：`体重体脂记录`

| 字段名 | 类型 | type值 | 备注 |
|--------|------|--------|------|
| 日期 | 日期 | 5 | 必填 |
| 体重（kg） | 数字 | 2 | |
| 体脂率（%） | 数字 | 2 | 填小数，如18.5 |
| 净肌量（kg） | 数字 | 2 | 体重×(1-体脂率/100) |
| 备注 | 文本 | 1 | |

创建示例：
```json
{
  "name": "体重体脂记录",
  "fields": [
    {"field_name": "日期", "type": 5},
    {"field_name": "体重（kg）", "type": 2},
    {"field_name": "体脂率（%）", "type": 2},
    {"field_name": "净肌量（kg）", "type": 2},
    {"field_name": "备注", "type": 1}
  ]
}
```

---

## 表 5：每日计划

表名：`每日计划`

基础字段（手动填写）：

| 字段名 | 类型 | type值 | 备注 |
|--------|------|--------|------|
| 日期 | 日期 | 5 | 必填，初始化时批量预填 |
| 碳日类型 | 单选 | 3 | 高碳日/中碳日/低碳日/极高碳日/极低碳日 |
| 热量目标（kcal） | 数字 | 2 | 按碳日类型填入 |
| 碳水目标（g） | 数字 | 2 | |
| 蛋白质目标（g） | 数字 | 2 | |
| 脂肪目标（g） | 数字 | 2 | |

公式字段（创建后用 update 写入公式，不能在 create 时传入）：

| 字段名 | 公式逻辑 |
|--------|---------|
| 实际热量（kcal） | 跨表 FILTER 饮食记录表，按日期 SUM 热量 |
| 实际碳水（g） | 同上，SUM 碳水 |
| 实际蛋白质（g） | 同上，SUM 蛋白质 |
| 实际脂肪（g） | 同上，SUM 脂肪 |
| 热量差值（kcal） | 热量目标 - VALUE(实际热量) |
| 碳水差值（g） | 碳水目标 - VALUE(实际碳水) |
| 蛋白质差值（g） | 蛋白质目标 - VALUE(实际蛋白质) |
| 脂肪差值（g） | 脂肪目标 - VALUE(实际脂肪) |
| 训练消耗（kcal） | 跨表 FILTER 训练记录表，按日期 SUM 消耗热量（仅「已完成」状态） |
| 净热量缺口（kcal） | 热量目标 - VALUE(实际热量) + VALUE(训练消耗) |

创建示例（基础字段）：
```json
{
  "name": "每日计划",
  "fields": [
    {"field_name": "日期", "type": 5},
    {"field_name": "碳日类型", "type": 3, "property": {"options": [
      {"name": "高碳日"}, {"name": "中碳日"}, {"name": "低碳日"},
      {"name": "极高碳日"}, {"name": "极低碳日"}
    ]}},
    {"field_name": "热量目标（kcal）", "type": 2},
    {"field_name": "碳水目标（g）", "type": 2},
    {"field_name": "蛋白质目标（g）", "type": 2},
    {"field_name": "脂肪目标（g）", "type": 2}
  ]
}
```

---

## 每日计划表公式字段写法

### 汇总实际摄入（跨表 FILTER + SUM）

```
bitable::$table[<饮食记录table_id>].FILTER(CurrentValue.$column[<饮食记录日期field_id>]=bitable::$table[<每日计划table_id>].$field[<每日计划日期field_id>]).$column[<目标营养素field_id>].SUM()
```

### 差值字段（目标 - 实际，正数=还差多少，负数=超标）

```
bitable::$table[<每日计划table_id>].$field[<目标字段field_id>]-VALUE(bitable::$table[<每日计划table_id>].$field[<实际字段field_id>])
```

> ⚠️ VALUE() 必须包裹实际字段，否则公式字段相减会报错。

---

## 注意事项

- 创建表时，第一个字段会自动成为主字段（文本类型）。如果第一个字段是日期，飞书会自动创建一个默认文本主字段，需要注意字段顺序。
- 建议先创建表，再用 `feishu_bitable_app_table_field` action=list 确认字段 ID，避免后续写入时字段名对不上。
- 单选字段的选项在创建时通过 `property.options` 传入，后续也可以用 `feishu_bitable_app_table_field` action=update 修改。
