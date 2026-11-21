---
id: "twitch-monopoly-multiplayer"
title: "Twitch Monopoly Multiplayer"
tagline: "Interactive 1920x1080 OBS Monopoly overlay with live Twitch chat commands, auctions, and bilingual UI."
category: "tool"
status: "production"
featured: false
badge: "OBS Studio Tool"
problemStatement: "Running interactive multiplayer board games with Twitch chat usually requires clunky third-party browser captures, cluttered UIs, or manual chat moderation. Streamers need a clean 1920x1080 OBS Browser Source with native chat commands, real-time auctions, configurable rules, and an unobstructed 520x520 chat zone."
technicalSolution: "A zero-build, single-file HTML5 broadcast application designed directly for OBS Studio Browser Sources, connecting to Twitch IRC over WebSockets with IRCv3 tags for subscriber/streamer routing. Supports 2 to 8 players, a complete 40-field board, live auctions, jail & building mechanics, Street Unlock bonuses, adjustable background opacity, bilingual UI (EN/DE), and full JSON backup/restore."
techStack:
  - "HTML5"
  - "CSS3"
  - "JavaScript"
  - "Twitch IRC WebSocket"
  - "LocalStorage"
architectureHighlights:
  - "Zero-dependency single-file architecture tailored for OBS Studio Browser Source and Interact window workflows"
  - "Full 40-field Monopoly ruleset for 2–8 players with streamer, chat, and subscriber-only player sources"
  - "Twitch IRC WebSocket client with IRCv3 tags, PING/PONG heartbeat, auth-error handling, and silent exponential-backoff reconnect"
  - "Scoped 1400x1032 overlays keeping the 520x520 OBS chat zone unobstructed during card popups, pause, and game-over screens"
screenshots:
  - "/screenshots/twitch-monopoly-multiplayer/01-overview.png"
  - "/screenshots/twitch-monopoly-multiplayer/02-feature.png"
  - "/screenshots/twitch-monopoly-multiplayer/03-detail.png"
links:
  chromeWebStore: ""
  demoUrl: ""
  githubUrl: "https://github.com/Mello2110/twitch-monopoly-multiplayer"
sandbox:
  enabled: false
  type: "none"
  embedUrl: ""
  notes: "Designed as a local 1920x1080 OBS Studio Browser Source overlay with Twitch IRC WebSocket integration."
stats:
  version: "v2.0.0"
---

# Twitch Monopoly Multiplayer

[![Status](https://img.shields.io/badge/Status-Active-emerald?style=flat-square)](#)
[![Version](https://img.shields.io/badge/Version-v2.0.0-blue?style=flat-square)](#)
[![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)](#)

> Interactive 1920×1080 OBS Monopoly overlay with live Twitch chat commands, auctions, and bilingual UI.

<p align="left">
  <a href="https://github.com/Mello2110"><b>Mellow Solutions on GitHub</b></a> &nbsp;|&nbsp;
  <a href="https://buymeacoffee.com/mellowsolutions"><b>Buy Me a Coffee</b></a>
</p>

---

## Problem & Motivation
Running interactive board games with a live Twitch audience typically forces streamers to screen-capture cluttered web games without real chat participation or clean stream framing. Streamers need a reliable, broadcast-ready `1920×1080` OBS Browser Source where viewers and subscribers can roll dice, buy streets, bid in auctions, and build houses directly via chat commands while keeping a dedicated `520×520` space unobstructed for an on-stream Twitch chat overlay.

## Technical Solution
**Twitch Monopoly Multiplayer** (`MonopolyProSystem.html`) is a zero-build, single-file broadcast tool built for OBS Studio:
- **Live Twitch Chat Gameplay:** Connects directly to `wss://irc-ws.chat.twitch.tv:443` with `CAP REQ :twitch.tv/tags`, routing commands (`!roll`, `!buy`, `!no`, `!bid 500`, `!build <street>`, `!bail`, `!card`, `!skip`, `!end`) to **Streamer**, **Chat**, or **Subs-only** player slots.
- **Complete 40-Field Monopoly Engine (2–8 Players):** Includes full movement, rent calculation, houses & hotels (even-build rules), voluntary and refusal auctions, Jail mechanics, Event & Community cards, Undo support, configurable phase timers, Auto-Play bot timeout mode, and the optional **Street Unlock Bonus** mode.
- **Customizable Board & Cards:** Rename every street, railroad, and utility or edit all 32 Event & Community card texts and effects directly inside the OBS Interact window.
- **Broadcast-Ready Overlays & Themes:** Features a unified Dark-Gold broadcast theme (`Inter` + `Barlow Condensed`), adjustable background opacity (`0–100%`) for transparent OBS scenes, live bilingual UI (`English` / `Deutsch`), and scoped `1400×1032` overlays that never cover the `520×520` chat area.

## Architecture & Tech Stack
- **Languages & Libraries:** Vanilla HTML5, CSS3 (custom properties & 1920×1080 broadcast grid), ES2022 JavaScript.
- **Core Architecture:**
  - **Storage Layer:** `localStorage` persistence (`monopolyConfig`, `monopolyState`, `monopolyCredentials`) with automatic schema migration and full JSON backup/restore.
  - **Network Layer:** Isolated Twitch IRC WebSocket client (`connectToChat()`) with `PING`/`PONG` heartbeat, silent exponential-backoff reconnect, and auth-error handling.
  - **UI & Controls:** Tabbed OBS-friendly settings drawer (*Twitch & Setup*, *Players & Board*, *Rules & Timers*, *Design & OBS*, *Backup*), OBS-compatible custom dropdowns & color pickers, and two-step inline confirmations for destructive actions.

## Installation & Usage
1. Download or clone the repository and locate `MonopolyProSystem.html`.
2. In **OBS Studio**, add a new **Browser** source, enable **Local file**, and select `MonopolyProSystem.html`.
3. Set the Browser Source resolution to **Width: `1920`**, **Height: `1080`**.
4. Right-click the source in OBS and open **Interact** → click the **Settings** gear icon:
   - **Twitch & Setup:** Enter your Twitch channel name and OAuth token (`chat:read` scope), choose your language (`EN`/`DE`), and click **Save & Connect**.
   - **Players & Board:** Configure 2–8 players (`streamer`, `chat`, or `subsOnly`), pick figures & colors, and optionally customize street names and cards.
   - **Rules & Timers / Design & OBS:** Adjust starting money, Free Parking / Tax modes, timers, Auto-Play, accent color, and background opacity.
5. Click **New Game** in the Streamer Controls panel (hotkeys: `U` Undo, `Space` / `P` Pause, `Esc` Close Menu) and let chat play with `!roll`, `!buy`, `!no`, `!bid <amount>`, `!build <name>`, `!bail`, `!card`, and `!end`.

## License & Disclaimer
Part of the **Mellow Solutions** portfolio. Provided under the MIT License as-is for non-commercial and personal utility.
