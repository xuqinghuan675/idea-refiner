# Idea Refiner

English | [中文](./README.md)

> Before you spend 30 hours coding, let AI interrogate the idea for 10 minutes.

A structured prompt for vague side-project ideas. Put a fuzzy idea in; get an MVP plan out — or a clear "do not write product code yet."

---

## Quick Start

1. Open [prompt.en.md](./prompt.en.md)
2. Replace the first line with your idea
3. Paste the whole prompt into Claude / ChatGPT / DeepSeek
4. In round three, it will ask for your single primary goal. That answer controls the rest of the conversation

---

## What It Does

| | Generic ChatGPT | Idea Refiner |
|---|---|---|
| Attitude | Helps you build whatever you said | Questions first, then decides whether to encourage or stop |
| Flow | You ask, it answers | It asks you one question per round, always with an escape option |
| Logic | Treats all projects the same | Branches by the project's primary goal: personal use, portfolio, revenue, or open-source influence |

---

## Example 1: Revenue Goal, Stopped Before Coding

Sample scenario based on real side-project conversations.

User input: *"A desktop app that organizes ID photos, receipts, and documents for regular people."*

---

**Round 0-1 — Motivation**

AI: In three sentences, why do you want to build this?

> My computer has ID photos, receipts, and contracts scattered everywhere. Finding them is annoying. I like small local desktop tools that do not upload private files anywhere.

AI: What could you do for this idea right now if you opened your computer?

> I could write down the classification rules and test them on a few files.

---

**Round 2 — Single Primary Goal**

AI: What is the single primary goal for this project right now? Pick one.

A. Personal use — it is valuable if I use it myself  
B. Portfolio — it is valuable if it proves my ability on GitHub/resume  
C. Revenue — it is valuable if someone pays for it  
D. Open-source influence — it is valuable if people star/install/use it  
E. None of the above; I will describe it

> C — revenue

---

**Round 3 — Core Interaction**

AI: What is the user's first action?

A. Choose a folder, scan it, review results, then archive  
B. Scan the whole disk and notify from the tray  
C. Drag loose files into the app  
D. Watch a folder and auto-archive new files  
E. None of the above; I will describe it

> A

---

**Round 4 — Classification Method**

AI: How should classification work?

A. Rules only: filename, dimensions, EXIF — fast and dependency-free  
B. Local AI model — better recognition, hundreds of MB larger  
C. Cloud API — most accurate, but violates "do not upload"  
D. Rules + OCR — more useful, but adds OCR dependency and packaging cost  
E. None of the above; I will describe it

> D

---

**Round 5 — User vs Buyer**

AI: Who uses this? Who pays for it? Are they the same person?

A. My parents use it, but I do not know if they would pay  
B. Office workers use and pay for it, but I have not validated willingness  
C. Small businesses might use and pay, but I have not talked to any  
D. Honestly, I cannot separate user and buyer yet  
E. None of the above; I will describe it

> D

---

**Round 6 — Current Alternative**

AI: How do people solve this today? Are there similar tools?

A. I researched similar tools, but they are not focused on IDs/receipts  
B. I vaguely know photo managers exist, but I have not used them  
C. I have not checked  
E. None of the above; I will describe it

> C

---

**Round 7 — Pricing and First Users**

AI: Where will the first paying users come from? How would you charge?

A. List it on a marketplace, one-time purchase  
B. Post an article, start free, then charge  
C. Give it to a small group free, use feedback to decide pricing  
D. I have not thought about it  
E. None of the above; I will describe it

> D

---

**Self-review**

The primary goal is revenue. At least three key items are empty: user/buyer, current alternative, pricing, and first-user path. Hard stop.

**AI output**

> I recommend that you do not write product code yet. Here is the diagnosis:
>
> - You picked revenue, but you cannot say who uses it or who pays for it
> - You have not checked how people solve this today
> - You have no pricing hypothesis and no first-user path
> - Your own pain is real, but "I am annoyed by this" and "someone will pay" are different claims
>
> What you can do now:
> 1. Search marketplaces and forums for "photo organizer", "receipt organizer", and "document organizer". Look for price, complaints, and actual demand.
> 2. Post: "How do you organize ID photos and receipts on your computer? Would you pay for auto-archiving?" Come back if you get 5 concrete replies.
>
> Do those first. If you still want to build it, come back.

---

## Example 2: Portfolio Goal, MVP Plan

User input: *"A CLI tool that turns a folder of Markdown files into a static documentation site with a sidebar."*

**Confirmed facts**

| Dimension | Decision |
|---|---|
| Single primary goal | Portfolio |
| Tool user | Developers who write docs |
| Portfolio viewer | GitHub visitors, recruiters, peer developers |
| Stack/time | Python, 5 hours per week |
| Technical boundary | Local CLI, static HTML output, GitHub Pages deploy |
| MVP boundary | No search, i18n, plugin system, custom domains, or hot reload |
| Showcase path | README GIF + live demo + short write-up |

**AI output**

> **One-sentence definition**: For developers who write docs, this CLI turns a Markdown folder into a static documentation site with sidebar navigation.
>
> **Risks**:
> - Technical risk is low
> - Scope risk is high: this is a portfolio project, not a MkDocs competitor
> - Presentation risk matters most. If the README does not show the value in 10 seconds, the project underperforms
>
> **Technical choice**: Python + Markdown library + Jinja2 templates + one CLI command
>
> **Implementation steps**:
> 1. Core conversion: Markdown to HTML + sidebar tree. Validation: works on one real folder.
> 2. Template system: two clean built-in themes. Validation: switch themes in under one minute.
> 3. GitHub Pages output. Validation: a live demo link works.
>
> **Not doing**: search, i18n, plugins, custom domains, hot reload
>
> **Showcase path**:
> - Put the value proposition and a 30-second terminal GIF above the fold
> - Generate docs for a real project and link the live demo
> - Write a short post: "Why I wrote a 200-line doc site generator instead of using Docusaurus"
>
> **Proof point**: CLI design, filesystem handling, template rendering, documentation, publishing
>
> **Success check**: If the README gets 3 stars, saves, or issues in one week, keep maintaining it. If not, the portfolio goal is still met.

---

## Core Design: Branch by Primary Goal

Round three forces one current primary goal. Secondary goals can be recorded, but they do not drive the judgment.

| | Personal Use | Portfolio | Revenue | Open-Source Influence |
|---|---|---|---|---|
| Depth | Light | Medium | Heavy | Heavy |
| User validation required | No | No | Yes | Yes |
| Competitor/current alternative required | No | No | Yes | Yes |
| Distribution required | No | Showcase path only | Yes | Yes |
| Hard-stop threshold | Very high | Medium | Low | Low |
| MVP output focus | Cut to your own need | Improve the showcase | Validate willingness to pay | Reduce star/install friction |

If the goal drifts mid-conversation, the prompt reconfirms the primary goal before continuing.

**This is not an idea killer. Personal-use projects are not punished for lacking a market.**

---

## Who It Is For

- Indie hackers with fuzzy side-project ideas
- Developers who often start building before defining the MVP
- People who need a sharp collaborator before writing code

## Who It Is Not For

- Teams that already have a clear PRD
- Non-technical projects such as community operations or offline services
- People who only want to hear "great idea"

---

## License

MIT
