# LUNA AiNinaBridge2

> ## ⚠️ PROTOTYPE — NOT A FINISHED PRODUCT / これはプロトタイプです
>
> **EN** — This is an early **prototype**, released to gather feedback. **It may not work correctly.** It can behave unexpectedly and it may contain bugs — including bugs that **move real hardware** (telescope mount, focuser, filter wheel). **Automatic imaging must be supervised: stay with the equipment and be ready to cut power. Unattended operation is not supported.** Provided "AS IS", without warranty of any kind. You use it entirely at your own risk.
>
> **JA** — これは、ご意見を集めるために公開する初期の**プロトタイプ**です。**正しく動作しない可能性があります。** 予期しない動作や不具合(**実際の機材(赤道儀・フォーカサー・フィルターホイール)を動かす不具合を含みます**)があるかもしれません。**自動撮影は必ず見守ってください。機材のそばにいて、いつでも電源を切れる状態にしてください。無人運転は想定していません。** 現状のまま(AS IS)提供し、いかなる保証もありません。ご利用は自己責任でお願いします。

An AI-controllable star chart combined with [N.I.N.A.](https://nighttime-imaging.eu/) mount / camera / focuser / filter-wheel control, exposed as a streamable-HTTP MCP server. Part of the LUNA telescope-control family.

星図をAIから操作でき、N.I.N.A. の赤道儀・カメラ・フォーカサー・フィルターホイールも制御できる MCP サーバーです(LUNA ファミリーの一員)。

## What it does / できること

- Star chart the AI can drive (view, marks, planets, meridian and safety zone lines)
- Mount GOTO / sync / stop through NINA's Advanced API, with a meridian-safe crossing procedure
- Plans: capture recipes with **Centering**, **Autofocus** and **Autoguide** steps, meridian-zone handling, safe return
- Live run log, Abort and Emergency Stop, sleep prevention while a Plan runs (Windows)

## Known limitations / 既知の制限

- Verified on the author's own equipment only (an NS-5000 mount via ASCOM + a direct LX200-style TCP link). Other mounts are untested.
- Plate-solve checks (start position, Centering) have **not yet been validated on the real sky**.
- Centering, Autofocus and the PHD2 Autoguide sequence are implemented but **not yet verified on real hardware**.
- The mount's internal clock / position has been seen to reset on its own during the author's tests; the cause is still under investigation.
- Unattended operation is not supported. If the PC sleeps or this program stops, the mount keeps tracking with nobody in control.

## Requirements / 必要なもの

- Windows PC (no separate install needed — Node.js is bundled inside the app)
- N.I.N.A. with the **Advanced API** plugin (default `http://localhost:1888`), equipment connected in NINA's own Equipment tab
- To try it without hardware: NINA's ASCOM/Alpaca **simulators** work for most of the features

## Run / 起動

Two `.exe` files are included — keep them together with `public/` in the same folder.

- **`AiNinaBridge2.exe`** — the star chart and NINA control panel by itself, for use on this PC (or your local network) only. No internet, no claude.ai/Grok, no PIN.
- **`AiNinaBridge2Connect.exe`** — adds claude.ai/Grok access (it starts `AiNinaBridge2.exe` for you). Shows a connector URL and a PIN; the first time, press the one button in the "Tunnel status" box to set up the internet connection (a small helper is downloaded once).

Double-click whichever one matches what you want. Your browser opens by itself — no other window appears. To stop, use the ⏻ Quit button on the page itself (closing the browser tab does not stop the program).

同梱の2つの`.exe`は、`public\`フォルダとまとめて同じフォルダに置いてください。

- **`AiNinaBridge2.exe`** — 星図とNINA操作パネルだけです。このPC(または同じネットワーク内)からのみ使えます。インターネット・claude.ai/Grok・PINは使いません。
- **`AiNinaBridge2Connect.exe`** — claude.ai/Grokからの接続を追加します(`AiNinaBridge2.exe`を自動で起動します)。接続用URLとPINが表示されます。初回だけ、「Tunnel status」欄のボタンを1回押してインターネット接続を準備してください(小さな補助プログラムを1回だけ取得します)。

使いたい方をダブルクリックしてください。ブラウザが自動で開きます(他の画面は出ません)。終了は画面上の⏻ Quitボタンで行います(ブラウザのタブを閉じただけでは止まりません)。

## License / ライセンス

Freeware — free to download and run, all rights otherwise reserved. Copyright (c) 2026 Nishioka Sadahiko. See [LICENSE](LICENSE). Bundled third-party components: see [THIRD_PARTY_LICENSES.md](THIRD_PARTY_LICENSES.md).

Not an official NINA project; not affiliated with or endorsed by N.I.N.A. / NINA は別の独立したアプリケーションで、本ソフトとは無関係です。
