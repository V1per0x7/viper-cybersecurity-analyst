<div align="center">

<img src="assets/viper-mark.svg" width="88" alt="VIPER mark">

# VIPER
### Cybersecurity Analyst — built for OpenAI Build Week

**Faster application-security work without trading away evidence, privacy, or control.**

[![OpenAI Build Week](https://img.shields.io/badge/OpenAI-Build%20Week%202026-10a37f?style=for-the-badge&logo=openai&logoColor=white)](https://openai.devpost.com)
[![Built with Codex](https://img.shields.io/badge/Built%20with-Codex%20%2B%20GPT--5.6-412991?style=for-the-badge)](https://openai.devpost.com)
[![Status](https://img.shields.io/badge/status-live%20demo-22c55e?style=for-the-badge)](#try-it-without-receiving-the-private-scanner)
[![License: view only](https://img.shields.io/badge/private%20source-judges%20only-ef4444?style=for-the-badge)](#)

<a href="{{VIPER_DEMO_URL}}"><strong>▶ Try the fixed-lab demo</strong></a>
&nbsp;·&nbsp;
<a href="#how-viper-works">Architecture</a>
&nbsp;·&nbsp;
<a href="#the-viper-standard">Engineering standard</a>
&nbsp;·&nbsp;
<a href="#gallery">Gallery</a>

</div>

<br>

<div align="center">
  <img src="assets/demo-flow.gif" width="820" alt="VIPER demo command center: capturing attacker and victim sessions, running a bounded scan, and watching it complete with a live execution trace">
</div>

<br>

## Why I built it

Security researchers have more tools than ever, but important findings still get lost in noise and disconnected output. I started VIPER to make the work faster without making it careless: understand the application, follow the workflow, keep evidence attached to the correct operation, and say *unknown* when the proof is not there.

That problem is becoming more urgent as companies build faster with AI. Orca Security's 2026 research across more than 1,200 production organizations reports that [81% of organizations running AI packages had at least one known vulnerability, while 99.9% of alerts with an available fix remained unpatched](https://orca.security/resources/blog/2026-state-of-ai-security-report-summary/).

## What VIPER does

VIPER brings discovery, workflow analysis, bounded testing, evidence, and reporting into one control plane. Instead of treating an application as a pile of unrelated URLs, it models observed operations and the relationships between them.

| | |
|---|---|
| 🔒 **Fixed scope, verified first** | Authorization is checked before any target work begins. |
| 🎭 **Real attacker/victim sessions** | The demo captures two distinct authenticated identities server-side — not a fake toggle. |
| 🧵 **Evidence stays attached** | Temporary values stay bound to the correct user, operation, occurrence, and request location. |
| 🛑 **Fails closed** | Cancellation, privacy, and verifier uncertainty all fail closed by default. |
| 🪟 **Narrow public projection** | Public output is a sanitized, allowlisted contract — never raw scanner state. |
| 📊 **Honest metrics** | Metrics describe work that actually happened; skipped or failed work is never counted as success. |

## Try it without receiving the private scanner

The public demo runs against one bundled OWASP Juice Shop instance, inside its own contained gateway.

- A real embedded browser lets you inspect the target lab directly — signup, login, browsing all work against the real application.
- Explicit **Capture Attacker Session** / **Capture Victim Session** controls perform real server-side authentication before the scan unlocks — no one-click theater.
- Multiple visitors are session-isolated: your captured identities are yours alone, and if someone else's scan is running you get a live, honest "in progress" status instead of a confusing error.
- There is no custom target field, credential upload, arbitrary proxy, production API, or access to private scanner logs.

<a id="gallery"></a>
## Gallery

<table>
<tr>
<td width="50%"><img src="assets/dashboard-overview.png" alt="Command center after a completed bounded scan"></td>
<td width="50%"><img src="assets/lab-browser.png" alt="Embedded browser inspecting the real bundled Juice Shop lab"></td>
</tr>
<tr>
<td align="center"><sub>Command center — completed scan, live metrics, sanitized execution trace</sub></td>
<td align="center"><sub>Fixed lab browser — the real target, no arbitrary navigation</sub></td>
</tr>
</table>

<div align="center">
  <img src="assets/mobile-overview.png" width="280" alt="VIPER demo command center on a mobile viewport">
  <br><sub>Fully responsive — same live state, phone or desktop</sub>
</div>

<a id="how-viper-works"></a>
## How VIPER works

```mermaid
flowchart LR
    V["Visitor"] -->|"fixed scope only"| GW["Narrow VIPER Gateway"]
    GW -->|"allowlisted routes"| LAB["Bundled OWASP Juice Shop"]
    GW -->|"start / cancel / capture"| RT["Demo Runtime<br/>(session-isolated)"]
    RT -->|"bounded stage plan"| SC["VIPER Scan Controller"]
    SC --> ST1["rate_limit"] --> ST2["recon"] --> ST3["correlation"] --> ST4["chain_detection"]
    ST4 --> VER["Verifier / Evidence"]
    VER -->|"sanitized projection only"| PUB["Public Findings"]
    PUB --> V
```

The Build Week work focused on the foundation beneath this flow: a canonical operation contract, real session capture, and per-visitor isolation between workflow steps. Codex and GPT-5.6 helped trace callers, challenge assumptions, write adversarial regressions, capture real network traffic to diagnose broken routes, and review analogous consumers. Important changes still had to pass focused, adjacent, static, container, and browser checks before shipping.

VIPER does **not** currently ship AI inside the scanner. AI assisted development during Build Week; privacy-safe product assistance remains future work.

<a id="the-viper-standard"></a>
## The VIPER Standard

**Proof before confidence. Quality before coverage. Strong foundations before more features.**

I would rather harden an existing pipeline until it is dependable than add ten checks that create noise, lose context, or cannot be verified. A gate with 1,635 passing tests and three failures is still a failure. The product is supposed to produce results people can trust, so its development follows the same rule.

## What comes next

The next steps are easier installation, deeper workflow understanding, team controls, audit history, safer secret handling, and enterprise deployment. Longer term, I want to add AI assistance that respects privacy and can be measured against the same evidence standard as the rest of VIPER.

VIPER is a long-term project. I believe it can become a dependable cybersecurity analyst for both security teams and companies that are moving too quickly to leave security until later.

---

<div align="center">
<sub>Only test systems you own or are explicitly authorized to assess. The public demo is intentionally locked to its bundled training lab.</sub>
<br><br>

[![Made with Python](https://img.shields.io/badge/Python-3.13-3776AB?style=flat-square&logo=python&logoColor=white)](#)
[![Docker](https://img.shields.io/badge/Docker-ready-2496ED?style=flat-square&logo=docker&logoColor=white)](#)
[![GitHub Codespaces](https://img.shields.io/badge/Runs%20on-GitHub%20Codespaces-181717?style=flat-square&logo=github&logoColor=white)](#)

</div>
