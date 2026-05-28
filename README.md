# PickYourTrail — AI Toolchain Config

Central config repo for the engineering AI toolchain.  
All models route via [OpenRouter](https://openrouter.ai).

## One-liner setup

Paste this into your terminal. It creates the directories and pulls both configs in one shot:

```bash
curl -fsSL --create-dirs -o ~/.config/kilo/kilo.jsonc https://raw.githubusercontent.com/pickyourtrail/ai-config/main/kilo/kilo.jsonc && curl -fsSL --create-dirs -o ~/.pi/agent/models.json https://raw.githubusercontent.com/pickyourtrail/ai-config/main/pi/models.json && echo "✅ Kilo + Pi config installed"
```

### Updating PI key

```bash
vi ~/.pi/agent/models.json 

#update the apiKey and save it
```

### Updating Kilo key

```bash
Settings -> Providers -> OpenRouter -> [KEY] -> save
```

That's it. No npm, no install step.

---

## What gets installed

| File | Destination | Purpose |
|------|-------------|---------|
| `kilo/kilo.jsonc` | `~/.config/kilo/kilo.jsonc` | Kilo Code model routing config |
| `pi/models.json` | `~/.pi/agent/models.json` | Pi Agent model assignments |

---

## Model assignments

| Role | Model | Why |
|------|-------|-----|
| Code generation | `minimax/minimax-m2.7` | 1M context, strong on long files |
| Planning / Orchestration | `z-ai/glm-5.1` | Reasoning-focused, cost-efficient |
| Debug / Ask / Quick edits | `moonshotai/kimi-k2.6` | Fast and cheap |
| Spare | `x-ai/grok-4.3` | Available for custom assignments |

---

## Updating configs

1. Edit `kilo/kilo.jsonc` or `pi/models.json` in this repo
2. Merge to `main`
3. Engineers re-run the one-liner above to pull the latest

To update your local config without reinstalling everything:

```bash
# Kilo only
curl -fsSL --create-dirs -o ~/.config/kilo/kilo.jsonc https://raw.githubusercontent.com/pickyourtrail/ai-config/main/kilo/kilo.jsonc

# Pi only
curl -fsSL --create-dirs -o ~/.pi/agent/models.json https://raw.githubusercontent.com/pickyourtrail/ai-config/main/pi/models.json
```

---

## Prerequisites

- OpenRouter API key — get one
- Set it in Kilo Code: `Settings → API Provider → OpenRouter → paste key`
- Set it in Pi Agent: `pi config set api-key <your-key>`
