# fat-loss-coach

A personal fat loss coach skill for [OpenClaw](https://openclaw.ai) — powered by AI, backed by Feishu (Lark) Bitable.

This skill turns your AI assistant into a fully functional fat loss coach: it initializes your profile, creates tracking spreadsheets, logs workouts and meals, auto-calculates nutritional gaps, and delivers daily/weekly/monthly reports — all driven by real data from your Feishu tables.

---

## What It Does

**One-time Setup**
- Collects your stats (gender, height, weight, age, body fat %, training habits)
- Recommends a diet plan based on your profile
- Calculates your TDEE and daily macro targets
- Auto-creates 5 Feishu Bitable tables
- Pre-fills your carb-cycling schedule for the next 2–4 weeks

**Daily Tracking**
- Log workouts → writes to Training Log + Exercise Detail tables simultaneously
- Log meals → calculates each food's macros independently, writes to Meal Log
- Log weight/body fat → writes to Body Composition table, calculates progress

**Auto Calculations (no manual work)**
- Daily Plan table auto-aggregates actual intake from Meal Log by date
- Shows target vs. actual for calories, carbs, protein, fat
- Calculates net caloric deficit (diet gap + training burn)

**Reports**
- Daily report at 21:00: training summary, nutrition gaps, strength progression tips, tomorrow's carb day
- Weekly report every Sunday: completion rate, avg intake, weight change, next week adjustments
- Monthly report: body composition trend, strength progress, ETA to goal

---

## Diet Plans

### Plan A: Kai Sheng Wang Method (Carb Cycling)
Moderate carb cycling for steady fat loss while preserving muscle. Best for most people with a training foundation.

- High carb days (2x/week): 50% of weekly carb budget → leg days
- Medium carb days (3x/week): 35% → regular training days
- Low carb days (2x/week): 15% → rest days

### Plan B: Tan Chengyi Method (Extreme Carb Cycling)
Aggressive cycling for faster fat loss. High execution discipline required.

- 4 days extreme low carb + 1 day extreme high carb
- High carb day: clean low-GI carbs only (sweet potato, oats, brown rice) — no cheat meals

---

## Tables Created

| Table | Purpose |
|-------|---------|
| 训练记录 (Training Log) | Daily workout overview: type, duration, calories burned |
| 动作明细 (Exercise Detail) | Per-exercise rows: name, sets, reps, weight |
| 饮食记录 (Meal Log) | Per-meal rows: food, calories, carbs, protein, fat |
| 体重体脂记录 (Body Composition) | Periodic measurements: weight, body fat %, lean mass |
| 每日计划 (Daily Plan) | Per-day targets + auto-aggregated actuals + gaps + net deficit |

---

## Requirements

- [OpenClaw](https://openclaw.ai) with Feishu (Lark) integration
- A Feishu account (free tier works)

---

## Installation

1. Clone this repo
2. Copy the `fat-loss-coach/` folder to your OpenClaw skills directory:
   ```bash
   cp -r fat-loss-coach/ ~/.openclaw/workspace-<your-bot>/.agents/skills/
   ```
3. Or install the `.skill` file directly via OpenClaw

---

## Usage

Just talk to your AI assistant naturally. The skill triggers automatically when you mention:

- Recording a workout: *"今天练胸，卧推70kg×8×4组"*
- Logging a meal: *"午饭吃了鸡胸肉200g、米饭150g"*
- Checking progress: *"我现在体重71kg，体脂17%"*
- Requesting a report: *"给我看今天的日报"*

For new users with no tables set up, the skill will guide you through the full initialization flow.

---

## License

MIT
