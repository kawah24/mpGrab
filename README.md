# mpGrab

**mpGrab** is a free, friendly video downloader and converter for Windows by [RockHouse](https://ko-fi.com/rockhouse).
Paste a link, pick a format, done — powered by the actively maintained **yt-dlp** engine.

## Download

Grab the latest installer from the [Releases page](https://github.com/kawah24/mpGrab/releases):

- `mpGrab-<version>-setup.exe` - per-user Windows installer (no admin needed, Start-menu + desktop shortcuts, uninstaller)
- `mpGrab-<version>-win64.zip` - portable zip, just unzip and run
## Features

- **Four clean tabs** — Search, Downloads, Settings, About
- **Search YouTube** directly and queue results with thumbnails
- **Formats**: Best quality, 1080p / 720p / 480p, MP3 192 kbit/s, M4A
- **Clean file names**: `Artist - Title` (uploader/channel fallback) with the thumbnail embedded as cover art
- **13 interface languages**: English, Deutsch, Türkçe, Español, Français, Italiano, Português, Русский, العربية, 中文, 日本語, 한국어, Nederlands
- **Dark & light themes** with four accent colors — persisted between runs
- **Settings**: output folder, metadata (ID3 tags), clipboard monitoring, notifications, browser-cookie login for YouTube, proxy support (with authentication), system-tray minimize, WebM preference, force IPv4
- **Download queue** with per-item progress, speed, ETA and cancel
- Graceful fallback when ffmpeg is not installed

## Quick start (from source)

```
py -3.12 -m venv .venv
.venv\Scripts\pip install -r requirements.txt
.venv\Scripts\python main.py
```

Or simply double-click `run.bat` (uses the bundled `.venv`).

## Build releases

- `build_exe.bat` — standalone `dist\mpGrab.exe` (PyInstaller one-file)
- `make_release.bat` — exe + installer (`dist\installer\mpGrab-1.1.0-setup.exe`) + portable zip (requires [Inno Setup 6](https://jrsoftware.org/isinfo.php))

## Project layout

```
main.py              entry point
core/config.py       persistent settings (%APPDATA%\mpGrab)
core/downloader.py   yt-dlp engine wrapper + download queue
core/search.py       YouTube search
core/i18n*.py        UI translations (13 languages)
ui/                  CustomTkinter interface (tabs, toasts, tray)
tests/               unit + GUI smoke tests
```

## Legal

mpGrab is provided "as is", without warranty of any kind. You are responsible for using it lawfully:
only download content you own or have permission to save, and respect each platform's terms and your
local copyright law. mpGrab does not collect or transmit any personal data — see `DISCLAIMER.txt`.

Support the project: ☕ [ko-fi.com/rockhouse](https://ko-fi.com/rockhouse)
