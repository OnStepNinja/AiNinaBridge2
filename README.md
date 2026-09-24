# LUNA AiNinaBridge2

> ## ⚠️ PROTOTYPE — NOT A FINISHED PRODUCT
>
> This is an early **prototype**, released to gather feedback. **It may not work correctly.** It can behave unexpectedly and it may contain bugs — including bugs that **move real hardware** (telescope mount, focuser, filter wheel). **Automatic imaging must be supervised: stay with the equipment and be ready to cut power. Unattended operation is not supported.** Provided "AS IS", without warranty of any kind. You use it entirely at your own risk.

An AI-controllable star chart combined with [N.I.N.A.](https://nighttime-imaging.eu/) mount / camera / focuser / filter-wheel control, exposed as a streamable-HTTP MCP server. Part of the LUNA telescope-control family. As of v0.8.1 it covers both ends of the hobby in one free app — fully automated imaging for GOTO mounts, and **LUNA AiPushTo**, a manual push-to mode for telescopes with no GOTO at all.

## What it does

- Star chart the AI can drive (view, marks, planets, meridian and safety zone lines)
- Mount GOTO / sync / stop through NINA's Advanced API, with a meridian-safe crossing procedure
- Plans: capture recipes with **Centering**, **Autofocus** and **Autoguide** steps, meridian-zone handling, safe return
- **🚀 LUNA AiPushTo mode** (new in v0.8.1) — continuously plate-solves through the same camera used for imaging so you can manually push **any** telescope onto a target, including a plain Dobsonian or alt-az mount with no GOTO. No phone, no extra hardware, no per-session calibration. Its own button switches the whole screen into a separate, uncluttered mode (only the chart, the solved position, and a way back) so it never gets confused with normal AiNinaBridge2 operation
- The AI acts as an **observing companion and imaging advisor**, not just a command executor — it can suggest targets for tonight based on conditions, comment on exposure/gain choices, and reacts to what it actually sees in a capture. A small cross-session **journal** lets it remember prior sessions in its own words instead of starting cold every time
- Live run log, Abort and Emergency Stop, sleep prevention while a Plan runs (Windows)

## Known limitations

- Verified on the author's own equipment only (an NS-5000 mount via ASCOM + a direct LX200-style TCP link, plus a NINA Simulator camera). Other mounts and cameras are untested.
- **AiPushTo mode is new and not yet validated on the real sky** — testing so far is against the NINA Simulator's fixed test image. Solve success rate and speed under real conditions are unknown; feedback is very welcome, especially from Dobsonian/alt-az/OnStep+SmartWebServer users.
- Plate-solve checks (start position, Centering) have **not yet been validated on the real sky**.
- Centering, Autofocus and the PHD2 Autoguide sequence are implemented but **not yet verified on real hardware**.
- The mount's internal clock / position has been seen to reset on its own during the author's tests; the cause is still under investigation.
- Unattended operation is not supported. If the PC sleeps or this program stops, the mount keeps tracking with nobody in control.

## Requirements

- Windows PC (no separate install needed — Node.js is bundled inside the app)
- N.I.N.A. with the **Advanced API** plugin (default `http://localhost:1888`), equipment connected in NINA's own Equipment tab
- To try it without hardware: NINA's ASCOM/Alpaca **simulators** work for most of the features

## Run

Two `.exe` files are included — keep them together with `public/` in the same folder.

- **`AiNinaBridge2.exe`** — the star chart and NINA control panel by itself, for use on this PC (or your local network) only. No internet, no claude.ai/Grok, no PIN.
- **`AiNinaBridge2Connect.exe`** — adds claude.ai/Grok access (it starts `AiNinaBridge2.exe` for you). Shows a connector URL and a PIN; the first time, press the one button in the "Tunnel status" box to set up the internet connection (a small helper is downloaded once).

Double-click whichever one matches what you want. Your browser opens by itself — no other window appears. To stop, use the ⏻ Quit button on the page itself (closing the browser tab does not stop the program).

## Support development

Free to use, no account or payment needed. That said, this is independently developed in the author's own time, and after about 3 months of use the app shows a small, dismissible reminder that a $5 coffee-tier contribution (💗 button, via PayPal) helps keep development going. Checking it off keeps the reminder quiet for a year. It is never required to keep using the app.

## License

Freeware — free to download and run, all rights otherwise reserved. Copyright (c) 2026 Nishioka Sadahiko. See [LICENSE](LICENSE). Bundled third-party components: see [THIRD_PARTY_LICENSES.md](THIRD_PARTY_LICENSES.md).

Not an official NINA project; not affiliated with or endorsed by N.I.N.A.
