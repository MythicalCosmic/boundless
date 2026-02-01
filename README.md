# Boundless

> The next generation Telegram bot framework — built to break limits

[![Python](https://img.shields.io/badge/Python-3.11+-3776AB?logo=python&logoColor=white)](https://python.org)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-In_Development-orange)]()
[![Redis](https://img.shields.io/badge/Redis-Supported-DC382D?logo=redis&logoColor=white)]()

**Boundless** is a next-generation Telegram bot framework built from the ground up. Designed for developers who need power, flexibility, and simplicity — all in one package.

> ⚠️ **Work in Progress** — Core framework is functional. More features and templates coming soon.

---

## 🎯 Vision

Build the most powerful, developer-friendly Telegram bot framework that exists. Period.

---

## ✨ Features

### Ready Now
- 🏗️ **Complete Framework** — Built from scratch, not a wrapper
- ⚡ **Redis Integration** — Caching, sessions, rate limiting
- 🛠️ **CLI Tools** — Project scaffolding and management
- 🗄️ **Database Layer** — Built-in ORM support
- 📦 **Type System** — Full type hints throughout
- 🔌 **Extensions** — Modular plugin architecture
- 🧪 **Test Suite** — Testing utilities included
- 📚 **Documentation** — Comprehensive docs

### Coming Soon
- 📋 **5+ Templates** — Pre-built bot templates out of the box
- 🔄 **Async & Sync** — Both paradigms supported
- 🎨 **Simpler FSM** — State management made easy
- 🌍 **i18n Built-in** — Internationalization by default
- 🔥 **Hot Reload** — Development mode with auto-restart
- 📊 **Analytics** — Built-in usage tracking
- 🛡️ **Rate Limiting** — Redis-powered throttling

---

## 🏗️ Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│                         BOUNDLESS                                │
│              Next Generation Bot Framework                       │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│   ┌──────────────────────────────────────────────────────────┐   │
│   │                      CLI                                 │   │
│   │            Project Generation • Commands                 │   │
│   └─────────────────────────┬────────────────────────────────┘   │
│                             │                                    │
│   ┌─────────────────────────▼────────────────────────────────┐   │
│   │                     CLIENT                               │   │
│   │              Bot Client • Connection                     │   │
│   └─────────────────────────┬────────────────────────────────┘   │
│                             │                                    │
│   ┌─────────────────────────▼────────────────────────────────┐   │
│   │                      CORE                                │   │
│   │         Router • Handlers • Middleware • Events          │   │
│   └─────────────────────────┬────────────────────────────────┘   │
│                             │                                    │
│   ┌─────────┬───────────────┼───────────────┬─────────┐         │
│   │         │               │               │         │         │
│   ▼         ▼               ▼               ▼         ▼         │
│ ┌─────┐ ┌──────┐ ┌──────────────┐ ┌─────┐ ┌─────────────┐      │
│ │ DB  │ │ EXT  │ │   TEMPLATES  │ │TYPES│ │    UTILS    │      │
│ │     │ │      │ │              │ │     │ │             │      │
│ │Redis│ │Plugin│ │ 5+ Pre-built │ │Hints│ │   Helpers   │      │
│ │SQL  │ │System│ │   Starters   │ │     │ │             │      │
│ └─────┘ └──────┘ └──────────────┘ └─────┘ └─────────────┘      │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

---

## 📁 Project Structure

```
boundless/
│
├── cli/                    # Command-line interface
│   ├── commands/          # CLI commands
│   └── generators/        # Project generators
│
├── client/                 # Bot client
│   ├── bot.py             # Main bot class
│   └── connection.py      # Telegram connection
│
├── core/                   # Framework core
│   ├── router.py          # Message routing
│   ├── handlers.py        # Handler management
│   ├── middleware.py      # Middleware system
│   └── events.py          # Event system
│
├── db/                     # Database layer
│   ├── redis.py           # Redis integration
│   ├── models.py          # Base models
│   └── session.py         # Session management
│
├── docs/                   # Documentation
│
├── examples/               # Example bots
│
├── ext/                    # Extensions/plugins
│   └── plugins/           # Plugin system
│
├── templates/              # Bot templates
│   ├── basic/             # Basic bot template
│   ├── shop/              # E-commerce bot
│   ├── support/           # Support ticket bot
│   ├── quiz/              # Quiz/game bot
│   └── admin/             # Admin panel bot
│
├── tests/                  # Test suite
│
├── types/                  # Type definitions
│   ├── message.py         # Message types
│   ├── user.py            # User types
│   └── callback.py        # Callback types
│
├── utils/                  # Utilities
│   ├── helpers.py         # Helper functions
│   └── validators.py      # Input validation
│
├── __init__.py            # Package init
├── __main__.py            # Entry point
├── LICENSE                # MIT License
└── README.md              # Documentation
```

---

## 📦 Installation

```bash
pip install boundless
```

Or install from source:

```bash
git clone https://github.com/MythicalCosmic/boundless.git
cd boundless
pip install -e .
```

---

## 🚀 Quick Start

### Create a New Bot

```bash
# Generate new project
boundless init my-bot --template basic

# Navigate to project
cd my-bot

# Configure
cp .env.example .env

# Run
python main.py
```

### Simple Bot Example

```python
from boundless import Bot, Router

bot = Bot(token="YOUR_TOKEN")
router = Router()

@router.command("start")
async def start(message):
    await message.reply("Hello from Boundless! 🚀")

@router.command("help")
async def help(message):
    await message.reply("I'm powered by Boundless framework")

bot.include_router(router)
bot.run()
```

### With Redis

```python
from boundless import Bot
from boundless.db import Redis

bot = Bot(token="YOUR_TOKEN")
redis = Redis(url="redis://localhost:6379")

@bot.command("count")
async def count(message):
    # Increment visit counter
    visits = await redis.incr(f"user:{message.from_user.id}:visits")
    await message.reply(f"You've visited {visits} times!")

bot.run()
```

### Using Templates

```bash
# Basic bot
boundless init my-bot --template basic

# E-commerce/shop bot
boundless init my-shop --template shop

# Support ticket system
boundless init my-support --template support

# Quiz/game bot
boundless init my-quiz --template quiz

# Admin panel bot
boundless init my-admin --template admin
```

---

## 🛠️ CLI Commands

| Command | Description |
|---------|-------------|
| `boundless init <name>` | Create new project |
| `boundless init <name> --template <t>` | Create from template |
| `boundless run` | Start bot |
| `boundless dev` | Start with hot reload |
| `boundless test` | Run tests |
| `boundless --version` | Show version |

---

## ⚙️ Configuration

```env
# Bot
BOT_TOKEN=your-bot-token

# Redis
REDIS_URL=redis://localhost:6379/0

# Database
DATABASE_URL=postgresql://user:pass@localhost:5432/boundless

# Settings
DEBUG=True
LOG_LEVEL=INFO
```

---

## 🔌 Extension System

```python
from boundless.ext import Extension

class AnalyticsExtension(Extension):
    def on_load(self):
        print("Analytics loaded!")
    
    async def on_message(self, message):
        # Track all messages
        await self.redis.incr("total_messages")

# Register extension
bot.add_extension(AnalyticsExtension())
```

---

## 🆚 Why Boundless?

| Feature | Boundless | aiogram | python-telegram-bot |
|---------|-----------|---------|---------------------|
| Built-in Redis | ✅ | ❌ | ❌ |
| CLI scaffolding | ✅ | ❌ | ❌ |
| 5+ templates | ✅ | ❌ | ❌ |
| Async + Sync | ✅ | Async only | Both |
| Extension system | ✅ | ✅ | ✅ |
| Type hints | ✅ | ✅ | ✅ |
| Simpler FSM | ✅ | Complex | Complex |
| Hot reload | ✅ | ❌ | ❌ |

---

## 📋 Roadmap

### Phase 1 — Core (Current)
- [x] Framework structure
- [x] CLI foundation
- [x] Client implementation
- [x] Core routing
- [x] Database layer
- [x] Type system
- [x] Extension system
- [x] Test setup

### Phase 2 — Templates
- [ ] Basic bot template
- [ ] Shop/e-commerce template
- [ ] Support ticket template
- [ ] Quiz/game template
- [ ] Admin panel template

### Phase 3 — Advanced
- [ ] Async + Sync support
- [ ] Hot reload dev mode
- [ ] Built-in analytics
- [ ] Rate limiting middleware
- [ ] Webhook support
- [ ] Documentation site

### Phase 4 — Ecosystem
- [ ] Plugin marketplace
- [ ] Community templates
- [ ] VS Code extension
- [ ] Dashboard UI

---

## 🤝 Contributing

This is an ambitious project and contributions are welcome!

1. Fork the repository
2. Create feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.

---

## 🌟 Star History

If you believe in this project, give it a ⭐ to show your support!

---

<p align="center">
  <b>Boundless</b> — The framework that breaks limits.
</p>
