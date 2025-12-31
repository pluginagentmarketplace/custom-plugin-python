<div align="center">

<!-- Animated Typing Banner -->
<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=28&duration=3000&pause=1000&color=2E9EF7&center=true&vCenter=true&multiline=true&repeat=true&width=600&height=100&lines=Python+Assistant;8+Agents+%7C+12+Skills;Claude+Code+Plugin" alt="Python Assistant" />

<br/>

<!-- Badge Row 1: Status Badges -->
[![Version](https://img.shields.io/badge/Version-2.0.0-blue?style=for-the-badge)](https://github.com/pluginagentmarketplace/custom-plugin-python/releases)
[![License](https://img.shields.io/badge/License-Custom-yellow?style=for-the-badge)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Production-brightgreen?style=for-the-badge)](#)
[![SASMP](https://img.shields.io/badge/SASMP-v1.3.0-blueviolet?style=for-the-badge)](#)

<!-- Badge Row 2: Content Badges -->
[![Agents](https://img.shields.io/badge/Agents-8-orange?style=flat-square&logo=robot)](#-agents)
[![Skills](https://img.shields.io/badge/Skills-12-purple?style=flat-square&logo=lightning)](#-skills)
[![Commands](https://img.shields.io/badge/Commands-4-green?style=flat-square&logo=terminal)](#-commands)

<br/>

<!-- Quick CTA Row -->
[📦 **Install Now**](#-quick-start) · [🤖 **Explore Agents**](#-agents) · [📖 **Documentation**](#-documentation) · [⭐ **Star this repo**](https://github.com/pluginagentmarketplace/custom-plugin-python)

---

### What is this?

> **Python Assistant** is a Claude Code plugin with **8 agents** and **12 skills** for python development.

</div>

---

## 📑 Table of Contents

<details>
<summary>Click to expand</summary>

- [Quick Start](#-quick-start)
- [Features](#-features)
- [Agents](#-agents)
- [Skills](#-skills)
- [Commands](#-commands)
- [Documentation](#-documentation)
- [Contributing](#-contributing)
- [License](#-license)

</details>

---

## 🚀 Quick Start

### Prerequisites

- Claude Code CLI v2.0.27+
- Active Claude subscription

### Installation (Choose One)

<details open>
<summary><strong>Option 1: From Marketplace (Recommended)</strong></summary>

```bash
# Step 1️⃣ Add the marketplace
/plugin add marketplace pluginagentmarketplace/custom-plugin-python

# Step 2️⃣ Install the plugin
/plugin install python-developer-plugin@pluginagentmarketplace-python

# Step 3️⃣ Restart Claude Code
# Close and reopen your terminal/IDE
```

</details>

<details>
<summary><strong>Option 2: Local Installation</strong></summary>

```bash
# Clone the repository
git clone https://github.com/pluginagentmarketplace/custom-plugin-python.git
cd custom-plugin-python

# Load locally
/plugin load .

# Restart Claude Code
```

</details>

### ✅ Verify Installation

After restart, you should see these agents:

```
python-developer-plugin:03-data-science
python-developer-plugin:02-web-development
python-developer-plugin:06-package-deployment
python-developer-plugin:01-python-fundamentals
python-developer-plugin:07-best-practices
... and 2 more
```

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🤖 **8 Agents** | Specialized AI agents for python tasks |
| 🛠️ **12 Skills** | Reusable capabilities with Golden Format |
| ⌨️ **4 Commands** | Quick slash commands |
| 🔄 **SASMP v1.3.0** | Full protocol compliance |

---

## 🤖 Agents

### 8 Specialized Agents

| # | Agent | Purpose |
|---|-------|---------|
| 1 | **03-data-science** | Data manipulation, analysis, and visualization with NumPy, P |
| 2 | **02-web-development** | Build web applications with Django, Flask, and FastAPI frame |
| 3 | **06-package-deployment** | Package creation, distribution, dependency management, and d |
| 4 | **01-python-fundamentals** | Master Python syntax, data types, control flow, functions, O |
| 5 | **07-best-practices** | PEP8, type hints, design patterns, performance optimization, |
| 6 | **05-async-concurrency** | Asynchronous programming with asyncio, threading, and multip |
| 7 | **04-testing-quality** | Unit testing, integration testing, mocking, and test-driven  |

---

## 🛠️ Skills

### Available Skills

| Skill | Description | Invoke |
|-------|-------------|--------|
| `pytest-testing` | Master test-driven development with pytest, fixtures, mockin | `Skill("python-developer-plugin:pytest-testing")` |
| `pandas-data-analysis` | Master data manipulation, analysis, and visualization with P | `Skill("python-developer-plugin:pandas-data-analysis")` |
| `asyncio-programming` | Master asynchronous programming with asyncio, async/await, c | `Skill("python-developer-plugin:asyncio-programming")` |
| `django-framework` | Build production-ready web applications with Django MVC, ORM | `Skill("python-developer-plugin:django-framework")` |
| `python-fundamentals` | Master Python syntax, data types, control flow, functions, O | `Skill("python-developer-plugin:python-fundamentals")` |
| `poetry-packaging` | Master Python package management with Poetry, dependency res | `Skill("python-developer-plugin:poetry-packaging")` |
| `python-performance` | Master Python optimization techniques, profiling, memory man | `Skill("python-developer-plugin:python-performance")` |

---

## ⌨️ Commands

| Command | Description |
|---------|-------------|
| `/skill-assessment` | assessment |
| `/project-builder` | builder |
| `/agent-guide` | guide |
| `/roadmap` | /roadmap |

---

## 📚 Documentation

| Document | Description |
|----------|-------------|
| [CHANGELOG.md](CHANGELOG.md) | Version history |
| [CONTRIBUTING.md](CONTRIBUTING.md) | How to contribute |
| [LICENSE](LICENSE) | License information |

---

## 📁 Project Structure

<details>
<summary>Click to expand</summary>

```
custom-plugin-python/
├── 📁 .claude-plugin/
│   ├── plugin.json
│   └── marketplace.json
├── 📁 agents/              # 8 agents
├── 📁 skills/              # 12 skills (Golden Format)
├── 📁 commands/            # 4 commands
├── 📁 hooks/
├── 📄 README.md
├── 📄 CHANGELOG.md
└── 📄 LICENSE
```

</details>

---

## 📅 Metadata

| Field | Value |
|-------|-------|
| **Version** | 2.0.0 |
| **Last Updated** | 2025-12-29 |
| **Status** | Production Ready |
| **SASMP** | v1.3.0 |
| **Agents** | 8 |
| **Skills** | 12 |
| **Commands** | 4 |

---

## 🤝 Contributing

Contributions are welcome! Please read our [Contributing Guide](CONTRIBUTING.md).

1. Fork the repository
2. Create your feature branch
3. Follow the Golden Format for new skills
4. Submit a pull request

---

## ⚠️ Security

> **Important:** This repository contains third-party code and dependencies.
>
> - ✅ Always review code before using in production
> - ✅ Check dependencies for known vulnerabilities
> - ✅ Follow security best practices
> - ✅ Report security issues privately via [Issues](../../issues)

---

## 📝 License

Copyright © 2025 **Dr. Umit Kacar** & **Muhsin Elcicek**

Custom License - See [LICENSE](LICENSE) for details.

---

## 👥 Contributors

<table>
<tr>
<td align="center">
<strong>Dr. Umit Kacar</strong><br/>
Senior AI Researcher & Engineer
</td>
<td align="center">
<strong>Muhsin Elcicek</strong><br/>
Senior Software Architect
</td>
</tr>
</table>

---

<div align="center">

**Made with ❤️ for the Claude Code Community**

[![GitHub](https://img.shields.io/badge/GitHub-pluginagentmarketplace-black?style=for-the-badge&logo=github)](https://github.com/pluginagentmarketplace)

</div>
