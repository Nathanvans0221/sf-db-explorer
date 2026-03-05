# Silver Fern DB Explorer

A Claude Code skill that lets anyone at Silver Fern query our legacy customer databases (PRODUCE, RESTOCK, ANALYZE) using plain English. No SQL knowledge required.

## What It Does

- **Connect** to any Silver Fern customer database (`{code}.silverfern.app`)
- **Ask questions** in plain English — Claude translates to SQL
- **Browse** customers, plant catalogs, schedules, sales data, store locations
- **Edit data** with a supervised preview → confirm workflow
- **Major changes** route to Nathan for approval via Teams

## Quick Setup

### 1. Install the skill

```bash
# Create the skill directory
mkdir -p ~/.claude/skills/db-explorer

# Download the skill file
curl -sL https://raw.githubusercontent.com/Nathanvans0221/sf-db-explorer/main/SKILL.md \
  -o ~/.claude/skills/db-explorer/SKILL.md
```

### 2. Install the dependency

```bash
pip3 install --break-system-packages pymssql
```

### 3. Use it

Open Claude Code and say:

```
/db-explorer
```

or

```
connect to cmg.silverfern.app
```

Claude will walk you through entering credentials and then you can start exploring.

## What You Can Ask

```
"How many customers do we have?"
"What's scheduled for next week?"
"Show me all mum combo varieties"
"What store locations are in Ohio?"
"Show sales data for the last 30 days"
```

Or use quick commands:
- `menu` — Show the quick start menu
- `tables` — List all tables
- `sample [table]` — Show 10 sample rows
- `count [table]` — Count rows

## Permission Levels

| Level | Access | How to Enter |
|-------|--------|-------------|
| **Explorer** (default) | Read-only SELECT queries | Automatic on connect |
| **Editor** | UPDATE + INSERT on approved tables | Type `elevate` |
| **Admin** | Adds DELETE (Nathan only) | Type `admin` |

Every write operation goes through: **preview affected rows → show exact SQL → type "confirm" → execute → verify**.

## Databases Covered

| Database | What's Inside |
|----------|--------------|
| **Produce** | Customers, plant catalogs, grow recipes, schedules, lots, greenhouse spaces, purchase orders |
| **Restock** | Store locations, sales data, product items, delivery schedules, replenishment orders |
| **Analyze** | Daily sales (Walmart/HD/Lowes/Kroger), retailer hierarchy, item costs |
| **MobileApp** | Physical counts, availability |

## Questions?

Ping Nathan in Teams or ask in the Product chat.
