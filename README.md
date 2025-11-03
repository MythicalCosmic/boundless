<div align="center">

<img src="https://raw.githubusercontent.com/MythicalCosmic/boundless/main/docs/logo.png" alt="Boundless logo" width="320"/>

# 🌀 Boundless  
**The next generation Telegram framework — built to break limits**

[![PyPI](https://img.shields.io/badge/PyPI-coming_soon-orange)](https://pypi.org/project/boundless/)
![Python](https://img.shields.io/badge/Python-3.9%2B-blue?logo=python)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)
![Status](https://img.shields.io/badge/status-alpha-lightgrey)

</div>

---

## 🚀 Why Boundless?

**Boundless** is a **clean, modern, and lightning-fast** Telegram bot framework that redefines what *developer-friendly* means —  
built for speed, simplicity, and pure joy.

| Feature | 🌀 Boundless | 🧩 aiogram |
|----------|--------------|-------------|
| **Core engine** | Pure async + optional sync bridge | Async only |
| **Performance** | ⚡ **~30% faster** in high-throughput tests | Baseline |
| **Redis integration** | First-class, zero-config support | Manual |
| **Magic filters** | `F.text == "hi"` — type-safe and IDE-friendly | `lambda m: m.text == "hi"` |
| **CLI scaffolding** | `python -m boundless new mybot` | None |
| **Built-in templates** | Minimal, FSM, Webhook, E-commerce, AI assistant 🤖 | None |
| **Middleware system** | Pre/post, rate-limit, logging, i18n, cache | Manual |
| **DB layer** | Async ORM + Alembic migrations out of the box | Manual setup |
| **AI integrations** | Gemini, OpenAI, Claude — *one-liner* setup | None |
| **Scheduler** | Built-in cron-style async scheduler | None |

---

## 🧠 Core Philosophy

1. **Zero boilerplate** — write *only* the logic that matters.  
2. **Async-first, sync-compatible** — your choice, no compromise.  
3. **Redis everywhere** — sessions, cache, rate limits, queues.  
4. **Developer joy** — intuitive CLI, hot reload, built-in REPL.  
5. **Boundless freedom** — everything is extendable, replaceable, and fast.

---

## ⚙️ Getting Started (while we polish)

```bash
# 1. Clone the repo
git clone https://github.com/MythicalCosmic/boundless.git
cd boundless

# 2. Install in editable mode with extras
pip install -e .[dev,ai,postgres,redis]

# 3. Create your first bot 🚀
python -m boundless new mybot
cd mybot
python bot.py
