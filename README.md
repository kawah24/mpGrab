# mpGrab

A friendly, themeable desktop video downloader for Windows by [RockHouse](https://ko-fi.com/rockhouse) — a ClipGrab-style
app built on the actively maintained **yt-dlp** engine (the same architecture
as ClipGrab: native GUI shell + battle-tested download engine underneath).

**Download the installer:** [mpGrap Releases](https://github.com/kawah24/mpGrap/releases)

*mpGrab — pluck videos off the web.*

## Features

**Four tabs, like ClipGrab:**
- **Search** — search YouTube, see thumbnail results with duration, queue any result.
- **Downloads** — paste a URL, pick a format, watch per-item progress / speed / ETA, cancel.
- **Settings** — seven sub-tabs: Folder, Metadata (ID3 tags + cover art), Clipboard monitoring (always download / ask / nothing), Notifications (each / all / never), Login (browser cookies for YouTube), Proxy (with authentication), Miscellaneous (remember quality, auto-remove finished, minimize to tray, prefer WebM, force IPv4) + a **Language** page with 13 languages (English, Deutsch, Türkçe, Español, Français, Italiano, Português, Русский, العربية, 中文, 日本語, 한국어, Nederlands).
- **About** — ☕ **Buy me a coffee** ([ko-fi.com/rockhouse](https://ko-fi.com/rockhouse)), credits, engine info.

Plus:
- **Clean file names**: `Evanescence - My Immortal.m4a` — uses artist metadata with uploader/channel fallback (instead of `Title [id]`).
- Dark & light themes with 4 accent colors — persisted between runs.
- Formats: Best, 1080p / 720p / 480p, MP3 192 kbit/s, M4A (ffmpeg-powered, DASH-merge aware).
- System-tray minimize, clipboard link detection, Windows toast notifications.
- Remembers your output folder and format; graceful fallback without ffmpeg.
- Upgrades seamlessly from a previous **VidGrab** install (settings are migrated).

## Quick start

Double-click **`run.bat`** — it uses the bundled `.venv` automatically.

Manual install (any Python 3.10+):

```
pip install customtkinter yt-dlp pystray
python main.py
```

## Configuration

Stored in `%APPDATA%\mpGrab\config.json`
(theme, accent color, output folder, last used format, language, proxy, …).
If `%APPDATA%\VidGrab\config.json` exists, it is imported automatically.

## Distribute

Run **`make_release.bat`** to produce both packages in one go:

- `dist\installer\mpGrab-1.1.0-setup.exe` — per-user Windows installer (no admin needed;
  Start-menu + optional desktop shortcut, uninstaller, badge on the setup exe)
- `dist\mpGrab-1.1.0-win64.zip` — portable zip (exe + disclaimer), just unzip and run

Requires Inno Setup 6 for the installer (`winget install JRSoftware.InnoSetup`); the zip step
needs nothing extra.

## Build a standalone .exe

Run **`build_exe.bat`** (installs PyInstaller into the venv on first use).
It produces **`dist\mpGrab.exe`** — a single file that needs no Python on
the target PC.

- First launch is slower (one-file builds self-extract to a temp dir).
- For MP3/M4A/merge support on machines without ffmpeg, drop `ffmpeg.exe`
  next to `mpGrab.exe` — it is detected automatically — or keep ffmpeg on PATH.
- Windows SmartScreen may warn about unsigned one-file builds; click
  "More info → Run anyway".

## Troubleshooting

- **Download fails / YouTube errors** — update the engine:
  `pip install -U yt-dlp`. YouTube changes frequently and yt-dlp ships fixes
  within days.
- **No MP3/M4A options** — install ffmpeg and make sure it is on PATH.

## Legal note

Only download content you own or have permission to save, and respect each
platform's terms of service and your local copyright law.
