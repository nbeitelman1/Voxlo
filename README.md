# Voxlo Android

Voxlo is an Android reading and listening app that combines ebook reading, text-to-speech conversion, audiobook playback, and in-app discovery/download flows.

It is built with Jetpack Compose and focuses on a smooth "read or listen" experience with persistent progress, configurable voices, and practical tooling like Kindle export helpers and barcode-based bookstore search.

---

## Features

### Reading
- EPUB/PDF/FB2 search and import flows.
- Reader with chapter navigation, progress tracking, and time-remaining estimates.
- Theme and typography controls (including curated font options).
- Mini-player integration while reading.

### Listening / TTS
- Convert ebook chapters to audio.
- Play converted audio with chapter awareness.
- Adjustable playback speed (0.1x to 5.0x).
- Edge + local TTS mode support.

### Audiobook Bay (ABB) Integration
- In-app ABB search screen.
- In-app torrent download pipeline (no external torrent app required).
- Cover fallback logic for missing artwork.
- ABB audio source selection in book details when available.

### Search and Discovery
- Anna's Archive search integration.
- Fallback cover resolution through Google Books.
- New barcode scanner flow (ISBN/EAN) for bookstore use:
  - scan barcode
  - resolve metadata
  - jump directly into in-app search

### Kindle Workflow
- Save EPUB to device.
- Send EPUB through email app to saved Send-to-Kindle address.
- Kindle email stored in Settings.
- EPUB sanitizer pipeline before send to improve compatibility.

---

## Tech Stack

- **Language:** Kotlin
- **UI:** Jetpack Compose (Material 3)
- **DI:** Hilt
- **Navigation:** Navigation Compose
- **Storage:** Room + DataStore
- **Networking:** OkHttp + Retrofit + Jsoup
- **Media:** AndroidX Media3 (ExoPlayer, Session)
- **Background work:** WorkManager
- **Torrent engine:** libtorrent4j (Android arm/arm64)
- **Barcode scan:** Google Play Services Code Scanner

---

## Requirements

- Android Studio (latest stable recommended)
- JDK 11
- Android SDK with:
  - `compileSdk = 35`
  - `minSdk = 24`
  - `targetSdk = 35`

---


## Troubleshooting

### Kindle send issues (E999)
Voxlo sanitizes EPUB structure before sending, but some source EPUBs may still fail Amazon conversion.

If a book fails:
- try another EPUB file of the same title
- use "Save EPUB to device" and test upload via official Send to Kindle web/app path
- verify your Kindle approved sender email in Amazon settings

### "No app can handle this action" for email send
- Ensure at least one email app is installed and configured.

### ABB download incomplete or wrong chapter count
- Retry with strong seeders.
- Some torrents have nested folders/mixed file layouts; keep app updated for latest ABB handling fixes.


---

## Legal / Content Notice

Users are responsible for complying with applicable copyright law and source terms when searching, downloading, converting, or sharing books/audiobooks.

This project provides tooling; it does not grant usage rights to copyrighted content.
