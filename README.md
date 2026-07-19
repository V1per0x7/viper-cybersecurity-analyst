<div align="center">

<img src="assets/viper-mark.svg" width="72" alt="VIPER mark">

# VIPER
### Cybersecurity Analyst — built for OpenAI Build Week

**Faster application-security work without trading away evidence, privacy, or control.**

<a href="{{VIPER_DEMO_URL}}"><strong>▶ Try the live demo</strong></a>
&nbsp;·&nbsp;
<a href="#how-viper-works">How it works</a>
&nbsp;·&nbsp;
<a href="#the-viper-standard">Engineering standard</a>

</div>

<br>

<div align="center">
  <img src="assets/viper-laptop-demo.gif" width="820" alt="VIPER dashboard: capturing attacker and victim sessions, running a bounded scan, and watching it complete live">
</div>

<div align="center">
<sub><strong>Real product, real footage.</strong> Every screen here is the actual dashboard running against a real, disposable OWASP Juice Shop instance — nothing staged.</sub>
</div>

<br>

## Why I built it

Security researchers have more tools than ever, but important findings still get lost in noise and disconnected output. I started VIPER to make the work faster without making it careless: understand the application, follow the workflow, keep evidence attached to the correct operation, and say *unknown* when the proof is not there.

That problem is becoming more urgent as companies build faster with AI. Orca Security's 2026 research across more than 1,200 production organizations reports that [81% of organizations running AI packages had at least one known vulnerability, while 99.9% of alerts with an available fix remained unpatched](https://orca.security/resources/blog/2026-state-of-ai-security-report-summary/).

## What VIPER does

VIPER brings discovery, workflow analysis, bounded testing, evidence, and reporting into one control plane. Instead of treating an application as a pile of unrelated URLs, it models observed operations and the relationships between them.

<table>
<tr><td width="26px">🔒</td><td><strong>Fixed scope, verified first</strong> — authorization is checked before any target work begins.</td></tr>
<tr><td>🎭</td><td><strong>Real attacker/victim sessions</strong> — the demo captures two distinct authenticated identities server-side, not a fake toggle.</td></tr>
<tr><td>🧵</td><td><strong>Evidence stays attached</strong> — temporary values stay bound to the correct user, operation, occurrence, and request location.</td></tr>
<tr><td>🛑</td><td><strong>Fails closed</strong> — cancellation, privacy, and verifier uncertainty all fail closed by default.</td></tr>
<tr><td>🪟</td><td><strong>Narrow public projection</strong> — public output is a sanitized, allowlisted contract, never raw scanner state.</td></tr>
<tr><td>📊</td><td><strong>Honest metrics</strong> — metrics describe work that actually happened; skipped or failed work is never counted as success.</td></tr>
</table>

## Try it without receiving the private scanner

The public demo runs against one bundled OWASP Juice Shop instance, inside its own contained gateway.

- A real embedded browser lets you inspect the target lab directly — signup, login, browsing all work against the real application.
- Explicit **Capture Attacker Session** / **Capture Victim Session** controls perform real server-side authentication before the scan unlocks.
- Multiple visitors are session-isolated: your captured identities are yours alone, and if someone else's scan is running you get a live, honest "in progress" status instead of a confusing error.
- There is no custom target field, credential upload, arbitrary proxy, production API, or access to private scanner logs.

<a id="how-viper-works"></a>

## How VIPER works

<div align="center">
  <img src="assets/architecture.svg" width="820" alt="VIPER architecture: fixed authorization enters a bounded control plane, producers normalize operations, evidence is verified, and only a sanitized projection reaches the public dashboard">
</div>

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
</div>
