# 🧬 transhumanists / milestones

> **Live dashboard:** [transhumanists.github.io](https://transhumanists.github.io)
> **API engine:** [transhumanists/apis](https://github.com/transhumanists/apis)

The canonical database of current highest-achieved milestones across the 7 verticals of human progress.

---

## 📊 Current Leaders

| Category | Top Milestone | Value | Source | Date |
|---|---|---|---|---|
| 🧬 Biotechnology | Alkermes reports pioneering ADHD data for orexin agonist | **—** | Alkermes | 2026-09-22 |
| 🧠 Computing & AGI | MMLU benchmark | **94.7%** | OpenAI GPT-6 | 2026-08-19 |
| ⚛️ Quantum Physics | Physical qubits (superconducting) | **4,158** | IBM Condor 2 | 2026-08-22 |
| ⚡ Energy | JT-60SA sustained yield | **100 MJ** | NIFS Japan | 2026-08-22 |
| 🛡️ Cybersecurity | Highest active CVSS score (0day) | **10.0 CRITICAL** | NVD / CISA | 2026-08-24 |
| 🚀 Spaceflight | Starship payload to LEO | **156 tonnes** | SpaceX | 2026-08-23 |
| 🌍 Defense | NATO rapid reaction force size | **300,000 personnel** | NATO HQ | 2026-08-15 |

---

## 📁 Data Files

| File | Purpose |
|------|---------|
| `Milestones.md` | This file — human-readable master list |
| `data/milestones.json` | Structured JSON — categories, subcategories, values, sources, geolocations |
| `data/events.json` | Geo-pinned events for the world map |
| `data/activity.json` | 30-day activity timeline + spike events |
| `data/world_layers.json` | Hand-authored overlay layers for the world map — 3 active conflict zones and 9 fleet-movement arrows |

---

## 🔄 How It Works

The pipeline runs every day (06:00 UTC) in `transhumanists/apis`, and can be
triggered manually via **Actions → Pipeline → Run workflow**:

1. **RSS scraper** pulls 80+ feeds (Nature, arXiv, IEEE, Phys.org, Reuters, SpaceNews, The Hacker News, ISW, CISA, NATO, SIPRI, ...). Higher-weight feeds contribute proportionally more articles.
2. **arXiv historical backfill** (opt-in): round-the-clock feeds only expose recent
   entries, so deeper history is pulled from the arXiv export API on demand.
   Set the `ARXIV_HISTORY_START` (YYYY-MM-DD, one-time month-by-month deep
   backfill) or `ARXIV_HISTORY_DAYS` (trailing window) repo variable to enable it.
   Every paper is stamped with its real arXiv `submittedDate` — nothing is ever
   backdated arbitrarily. Disabled by default, so routine runs cost nothing.
3. **LLM scorer** extracts structured milestone data: category, subcategory, value, unit, source, date, geolocation. Milestones are sorted **newest-first by date** within each category, so backfilled older milestones settle naturally lower down the list (`1970-01-01` is the sentinel for undated entries).
4. **Self-healer** validates feed URLs, replaces dead feeds with known-good alternatives
5. **Dashboard updater** commits `milestones.json`, `events.json`, `activity.json` to this repo and `transhumanists.github.io`
6. **Facebook poster** posts a daily digest to [facebook.com/transhumanistsBE](https://facebook.com/transhumanistsBE)

---

## 🤝 Contributing

Found a new record? Open an issue with:
- Source (publication, government filing, press release)
- Category and subcategory
- Numeric value and unit
- Date of publication

---

*Managed by [FrenzyPenguin Media](https://frenzypenguin-media.github.io) · A [neohiro](https://github.com/neohiro) project*


---

## 🔗 Related & Sponsorship

- 💖 [Sponsor neohiro on GitHub](https://github.com/sponsors/neohiro) — covers API + hosting costs
- 🌐 [neohiro.github.io](https://neohiro.github.io/) — main site
- 🎬 [FrenzyPenguin Media](https://frenzypenguin-media.github.io/) — video deep-dives
- 🧬 [transhumanists](https://transhumanists.github.io/) — companion dashboard for human progress

[![Visitors](https://api.visitorbadge.io/api/visitors?path=github.com/transhumanists/milestones&label=Visitors&countColor=%23263759)](https://visitorbadge.io/status?path=github.com/transhumanists/milestones)
