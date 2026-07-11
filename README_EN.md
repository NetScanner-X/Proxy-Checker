<div align="center">

[🇬🇧 English](./README_EN.md) | [🇮🇷 فارسی](./README_FA.md)

</div>

<div align="center">

# 🛡️ Proxy Pro Advanced

**All-in-one proxy collector, tester & sorter — Smart • Fast • Modern**

![version](https://img.shields.io/badge/version-1.0.7-9d4edd?style=for-the-badge)
![node](https://img.shields.io/badge/node-%3E%3D18-3fbf3f?style=for-the-badge&logo=node.js&logoColor=white)
![platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-00b8d9?style=for-the-badge)
![license](https://img.shields.io/badge/license-MIT-orange?style=for-the-badge)

*Collect from any source • Two-Phase testing • Protocol / Anonymity / Country detection • Auth proxies fully supported*

</div>

---

## ✨ What is Proxy Pro Advanced?

**Proxy Pro Advanced** is a professional command-line tool that turns raw proxy links into a **clean, tested, sorted, ready-to-use** list.
Give it URLs, local files, or just paste anything — it will collect, deduplicate, TCP-filter, protocol-test, measure latency, detect anonymity and country, and save everything into neat folders you never have to overwrite.

> Works on Windows, macOS and Linux. No accounts. No cloud. 100% local.

---

## 🚀 Highlights

| Feature | What it does |
|---|---|
| 🧠 **Smart Collector** | Pull proxies from URLs, files, folders, or paste inline (`ip:port`, `ip:port:user:pass`) |
| 🔒 **Private Sources** | Sources that carry their own `username:password` — kept isolated from public/auto |
| ⚡ **Two-Phase Testing** | Phase 1: TCP reachability → Phase 2: full protocol test (http/https/socks4/socks5) |
| 🕵️ **Anonymity Check** | Detects Transparent / Anonymous / Elite proxies |
| 🌍 **Geo Lookup** | Country + ISP per proxy |
| 🔑 **Auth Proxies** | Full `user:pass` preserved in `alive_with_auth.txt` |
| 💾 **Numbered History** | Every Collect/Test creates a new folder — nothing is ever overwritten |
| ▶️ **Resume** | Stop with `Q` / `Ctrl+C`, continue next run from exactly where you left off |
| 🎨 **Modern UI** | Colored panels, live progress, purple/cyan status bar |

---

## 📦 Installation

### 1️⃣ Install Node.js (once)
Download **Node.js 18+** from [nodejs.org](https://nodejs.org) and install with default options.

### 2️⃣ Get the tool
Download the ZIP from the [Releases](../../releases) page and extract it anywhere.

### 3️⃣ Install dependencies
**Windows:** double-click `INSTALL_FIRST.bat`
**macOS/Linux:**
```bash
npm install
```

### 4️⃣ Run
**Windows:** double-click `RUN.bat`
**macOS/Linux:**
```bash
node proxy-pro.js
```

---

## 🎛️ Main Menu

At the top you see the live status bar:

```
Mode : balanced   Two-Phase: on   Conc: 150   Anon: on   Geo: on
```

| Key | Action | What it does |
|:---:|---|---|
| `1` | **Add sources** | Add Public / Private / Smart-Paste sources |
| `2` | **Manage sources** | View & remove saved sources |
| `3` | **Collect proxies** | Fetch from sources (see submenu below) |
| `4` | **Test proxies** | Test the last collected list (asks for mode first) |
| `5` | **Settings / Modes** | Change test mode and manual knobs |
| `6` | **Open output folder** | Jump to alive / best / csv / HTML report |
| `H` | **Help** | Full in-app guide |
| `0` | **Exit** | Quit cleanly |

---

## ➕ Add Sources (menu 1)

| Key | Type | Description |
|:---:|---|---|
| `1` | **Public** | URLs or local files, no credentials |
| `2` | **Private** | URL/file + `username:password` for that source |
| `3` | **Smart Paste** | Paste ANYTHING — URLs, files, `ip:port`, `ip:port:user:pass`. Auto-routed. |
| `0` | Back | |

You can drag & drop multiple files, or drop an entire folder (all `.txt` / `.list` / `.csv` inside are added).

---

## 📥 Collect Proxies (menu 3)

| Key | Source | Notes |
|:---:|---|---|
| `1` | **Public sources** | Only URLs/files you added via Add sources → Public |
| `2` | **Private sources** | Only sources with `user:pass` (isolated) |
| `3` | **Smart Paste** | Only proxies you added via Smart Paste |
| `4` | **Auto (built-in)** | Uses the built-in default list — nothing saved to your sources |
| `5` | **Both (merged)** | Public + Smart Paste **and then** the built-in defaults. **Private is intentionally NOT included** — use option 2 for that. |
| `0` | Back | |

---

## 🧪 Test Proxies (menu 4)

Before every test run you get:

| Key | Choice |
|:---:|---|
| `1` | Use the **current mode** from Settings |
| `2` | **AUTO-pick** based on list size |
| `3` | **Choose manually** from the 8 modes below |
| `0` | Cancel |

### Test modes

| Mode | Best for | Conc | Highlights |
|---|---|:---:|---|
| **ultra** | 100k+ lists | 400 | Max speed, no anon/geo |
| **fast** | Large lists | 250 | 1 endpoint + geo |
| **balanced** ⭐ | Default | 150 | 2 endpoints + anon + geo |
| **accurate** | Quality first | 80 | 3 endpoints, double-check |
| **deep** | Lowest false-dead | 50 | 8 endpoints, judge revalidated |
| **strict** | Only the best | 60 | Very high thresholds |
| **lowpc** | Weak PC / slow net | 30 | Lightweight |
| **sample** | Sanity check | 120 | First 1000 only |

Press `Q` or `Ctrl+C` any time — partial results are saved and resumable.

---

## 📁 Output Layout (nothing is ever overwritten)

```
output/
├── All_proxy/
│   └── All_proxy_N/
│       ├── all_proxies.txt        ← every collected proxy
│       ├── ip_port_only.txt       ← plain ip:port
│       ├── http.txt / https.txt / socks4.txt / socks5.txt / unknown.txt
│       └── collect_summary.txt
└── Result_test/
    └── results_N/
        ├── alive.txt              ← working proxies WITHOUT auth (best → worst)
        ├── alive_with_auth.txt    ← working proxies WITH full user:pass
        ├── best.txt / elite.txt   ← top-tier only
        ├── dead.txt
        ├── results.csv / summary.txt / tested_results.json / report.html
        ├── by_type/               ← http / https / socks4 / socks5
        └── by_country/            ← US.txt / DE.txt / IR.txt ...
```

> 💡 `alive_with_auth.txt` shows the **full** `user:pass` in plain text — it is your file, on your machine.

---

## 🩺 Troubleshooting

<details>
<summary><b>The menu doesn't react when I press a number</b></summary>

Fixed in **v1.0.7** — the input focus issue on some Windows terminals is gone. If you still see it, run from `cmd.exe` or Windows Terminal (not from inside another wrapper) and press Enter after your choice.
</details>

<details>
<summary><b>Auto-collect (option 4) uses my private proxies</b></summary>

It doesn't — since **v1.0.5**, options `4` and `5` **never** touch Private sources. Use option `2` to run Private on its own.
</details>

<details>
<summary><b>All proxies look "dead"</b></summary>

Try a different mode (`deep` or `accurate`), check your internet/VPN, or open Settings → Test URLs and swap the endpoints.
</details>

---

## 💬 Contact

Questions, feedback, or ideas?
Reach out on Telegram → **[@Hunter23_S](https://t.me/Hunter23_S)**

---

<div align="center">

### ⭐ Enjoying Proxy Pro Advanced?
**Please give this repo a star — it really helps!** ⭐

</div>
