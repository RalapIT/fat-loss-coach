# fat-loss-coach

[English](#english) | [中文](#中文)

---

<a name="english"></a>
## English

A personal fat loss coach skill for [OpenClaw](https://openclaw.ai) — powered by AI, backed by Feishu (Lark) Bitable.

This skill turns your AI assistant into a fully functional fat loss coach: it initializes your profile, creates tracking spreadsheets, logs workouts and meals, auto-calculates nutritional gaps, and delivers daily/weekly/monthly reports — all driven by real data from your Feishu tables.

### What It Does

**One-time Setup**
- Collects your stats (gender, height, weight, age, body fat %, training habits)
- Recommends a diet plan based on your profile
- Calculates your TDEE and daily macro targets
- Auto-creates 6 Feishu Bitable tables (including a personal branded food library)
- Pre-fills your carb-cycling schedule for the next 2–4 weeks

**Daily Tracking**
- Log workouts → writes to Training Log + Exercise Detail tables simultaneously
- Log meals → looks up macros from your branded food library or the built-in food reference table, then writes to Meal Log
- Log weight/body fat → writes to Body Composition table, calculates progress

**Smart Nutrition Lookup (3-tier priority)**
1. Personal branded food library (your saved products with label data — most accurate)
2. Built-in food reference table (`references/food-nutrition.md`, 200+ common foods)
3. Web search as fallback — new results are saved to your food library

**Auto Calculations (no manual work)**
- Daily Plan table auto-aggregates actual intake from Meal Log by date
- Shows target vs. actual for calories, carbs, protein, fat
- Calculates net caloric deficit (diet gap + training burn)

**Reports**
- Daily report at 21:00: training summary, nutrition gaps, strength progression tips, tomorrow's carb day
- Weekly report every Sunday: completion rate, avg intake, weight change, next week adjustments
- Monthly report: body composition trend, strength progress, ETA to goal

### Diet Plans

**Plan A: Kai Sheng Wang Method (Carb Cycling)**
Moderate carb cycling for steady fat loss while preserving muscle.
- High carb days (2x/week): leg days
- Medium carb days (3x/week): regular training days
- Low carb days (2x/week): rest days

**Plan B: Tan Chengyi Method (Extreme Carb Cycling)**
Aggressive cycling for faster fat loss. High execution discipline required.
- 4 days extreme low carb + 1 day extreme high carb
- High carb day: clean low-GI carbs only (sweet potato, oats, brown rice) — no cheat meals

### Requirements

- [OpenClaw](https://openclaw.ai) with Feishu (Lark) integration
- A Feishu account (free tier works)

### Installation

**Option 1: Copy directory**
```bash
git clone https://github.com/RalapIT/fat-loss-coach.git
cp -r fat-loss-coach/ ~/.openclaw/workspace-<your-bot>/.agents/skills/
```

**Option 2: Install .skill file**

Download `fat-loss-coach.skill` from [Releases](https://github.com/RalapIT/fat-loss-coach/releases) and place it in your skills directory.

### Usage

Just talk to your AI assistant naturally:

```
# Log a workout
Today I trained chest: bench press 70kg×8×4 sets, 60 minutes total

# Log a meal
Lunch: 200g chicken breast, 150g rice, 100g broccoli

# Log a branded product
I had a Subway sandwich (check the label: 492kcal, protein 22.5g, carbs 50.4g, fat 21.9g)

# Log weight
Morning weight: 71.2kg, body fat 17.5%

# Get a report
Show me today's daily report
```

### Compatible Agents

- **Claude Code** (Anthropic official CLI)
- **OpenClaw** built-in Agent
- Any AI agent supporting the AgentSkills format

---

<a name="中文"></a>
## 中文

一个专为 [OpenClaw](https://openclaw.ai) 设计的 AI 减脂教练 Skill，数据驱动，飞书多维表格作为后端。

### 功能概览

**一次性初始化**
- 收集基础数据（性别、身高、体重、年龄、体脂率、训练习惯）
- 推荐减脂方案（凯圣王碳水循环 / 谭成义极端碳水循环）
- 计算 TDEE 和每日三大营养素目标
- 自动创建 6 张飞书多维表格（含个人品牌食品库）
- 根据训练计划预排 2~4 周碳日安排，批量写入表格

**日常记录（发数据即记录，无需额外指令）**
- 发训练数据 → 同步写入训练记录表 + 动作明细表
- 发饮食数据 → 三级优先查询营养素（品牌食品库 → 内置食物表 → web_search），写入饮食记录表
- 发体重/体脂 → 写入体重体脂记录表，计算距目标差距

**营养素查询三级优先级**
1. **个人品牌食品库** — 你保存过的有包装标签的食品（最准确）
2. **内置食物参考表**（`references/food-nutrition.md`，覆盖 200+ 常见食物）
3. **Web 搜索兜底** — 查到后自动补录入食品库

**自动汇总（无需手动操作）**
- 每日计划表按日期自动汇总实际摄入
- 自动计算目标 vs 实际差值
- 自动计算净热量缺口（饮食缺口 + 训练消耗）

**定期报告**
- 日报（每天 21:00）：训练/饮食完成情况、差值、重量进阶建议、明日碳日提示
- 周报（每周日）：训练完成率、平均摄入、体重变化、下周建议
- 月报（每月末）：体成分趋势、力量进步、预计达标时间

### 减脂方案

**方案 A：凯圣王模式（碳水循环）**
温和碳水波动，保肌减脂，适合大多数有训练基础的人。
- 高碳日（2天）→ 腿日
- 中碳日（3天）→ 普通训练日
- 低碳日（2天）→ 休息日

**方案 B：谭成义模式（极端碳水循环）**
激进减脂，执行要求高，严禁欺骗餐。
- 4天极低碳日 + 1天极高碳日循环
- 极高碳日只吃干净低GI碳水（红薯/燕麦/糙米）

### 环境要求

- [OpenClaw](https://openclaw.ai)（支持 Claude Code 或其他 AI Agent）
- 飞书账号（免费版即可）
- 已配置飞书插件（openclaw-lark）

### 安装方法

**方式一：复制目录**
```bash
git clone https://github.com/RalapIT/fat-loss-coach.git
cp -r fat-loss-coach/ ~/.openclaw/workspace-<你的bot名>/.agents/skills/
```

**方式二：安装 .skill 文件**

从 [Releases](https://github.com/RalapIT/fat-loss-coach/releases) 下载 `fat-loss-coach.skill`，放入 skills 目录即可。

### 使用方式

直接和 AI 助手对话，Skill 自动触发：

```
# 记录训练
今天练胸，卧推70kg×8×4组，上斜哑铃25kg×10×3组，练了60分钟

# 记录饮食（通用食物）
午饭吃了鸡胸肉200g、米饭150g、西兰花100g

# 记录饮食（品牌食品，带标签数据）
午饭吃了Subway三明治（492kcal，蛋白质22.5g，碳水50.4g，脂肪21.9g）

# 记录体重
今天早上空腹体重71.2kg，体脂17.5%

# 查看报告
给我看今天的日报
```

### 适用 Agent

- **Claude Code**（Anthropic 官方 CLI）
- **OpenClaw** 内置 Agent
- 其他支持 AgentSkills 格式的 AI Agent

---

## License

MIT
