<div align="center">

# 🦉 MYRA

**My Redact Assistant**

*I see what your files hide.*

A privacy-first tool that reads, edits, adds and removes hidden metadata in your files —
entirely in your browser. No accounts. No uploads. No servers.

[**Try it live →**](https://claude.ai/artifact/2dchFVkSFBXYdMVwaXqRUX)

![No backend](https://img.shields.io/badge/backend-none-1B1B1A)
![100% client-side](https://img.shields.io/badge/runs-100%25%20client--side-1B1B1A)
![Version](https://img.shields.io/badge/version-1.5-1B1B1A)
![License](https://img.shields.io/badge/license-MIT-1B1B1A)

</div>

---

## Why MYRA

Every photo you take can carry the GPS coordinates of where it was shot. Every PDF remembers
who created it, what software touched it last, and when. Every Word document can include a
full history of tracked changes and reviewer comments — invisible until someone goes looking.

MYRA finds all of that, shows it in plain language, and lets you change or clear it before you
share the file — without the file ever leaving your device.

## What it does

| | |
|---|---|
| 🔍 **Finds** | Identity, origin, timeline, content and security metadata, grouped and explained — not a raw property dump |
| ✏️ **Edits** | Change any field directly in the Metadata editor |
| ➕ **Adds** | Every editable field for the format is always listed. If the file doesn't have a value yet, press **Add** and write one |
| 🗑️ **Removes** | Remove any single field, with Undo before you export |
| 🔐 **Unlocks** | Opens password-protected PDFs (blank, user or owner password) for full editing |
| 🔒 **Protects** | Sets a new password on a PDF in the Security section before export |
| 👁️ **Previews** | Image preview, video frame, PDF page and document text, with an option to open the original |
| 🌗 **Themes** | AMOLED dark mode and a clean light mode, with one toggle |

Exports keep the **original file name**, and your original file is never modified.

## Supported formats

| Format | Editable fields | Notes |
|---|---|---|
| **JPG** | Author, Copyright, Camera make, Camera model, Software, Created, Modified | GPS location and embedded thumbnail can be removed |
| **PNG** | Title, Author, Copyright, Description, Comment, Software, Source, Creation Time, plus any existing text chunks | Compressed/international text chunks are shown read-only |
| **PDF** | Title, Author, Subject, Creator, Producer, Keywords, Created, Modified | Password unlock and password-protect on export |
| **DOCX** | Title, Author, Last modified by, Company, Application, Template, Created, Modified | Tracked changes and comments are detected and shown, but can't be removed yet |
| **MP4** | Created, Modified | Written in place — no re-encoding, nothing else in the file changes. Duration is read-only |

Dates are entered as `YYYY-MM-DD HH:MM:SS` (a plain `YYYY-MM-DD` also works).

## Privacy, by construction

MYRA has no backend. There is nothing to upload to, because nothing runs on a server — the
whole application is one static HTML file. Every parse, edit and export happens in memory, in
your browser tab, and disappears when you close it.

The only network requests MYRA makes are to load its open-source parsing libraries from a CDN
on first load. Your files are never part of any request.

## Getting started

**Use it instantly** — no install, no build step:
👉 **[claude.ai/artifact/2dchFVkSFBXYdMVwaXqRUX](https://claude.ai/artifact/2dchFVkSFBXYdMVwaXqRUX)**

**Or run it yourself:** download `index.html` from this repository and open it in a browser.
That's all — no `npm install`, no build, no server.

**Host your own copy:** turn on GitHub Pages (Settings → Pages → deploy from `main` / root)
and you'll have a live link in about a minute.

## How it works

Plain HTML, CSS and JavaScript in a single file, with four small libraries loaded from a CDN:

- [**piexifjs**](https://github.com/hMatoba/piexifjs) — JPEG EXIF read/write
- [**pdf-lib**](https://pdf-lib.js.org/) — PDF metadata read/write
- [**pdf.js**](https://mozilla.github.io/pdf.js/) — PDF rendering and password-protected PDF support
- [**JSZip**](https://stuk.github.io/jszip/) — DOCX (zip-based) read/write

PNG chunk handling, MP4 header patching and PDF password handling (RC4-128, following the PDF
spec's standard security handler) are implemented directly, with no dependency.

## Known limitations

- PDF password protection on export uses RC4-128 — widely supported, but not the newer AES-256.
- PDFs encrypted with AES-256 (PDF 2.0) can be viewed but not unlocked for editing yet.
- DOCX tracked changes and comments are shown but can't be removed yet.
- MP4 editing covers the container's Created/Modified timestamps only.
- EXIF text fields hold Latin-1 characters; other characters are converted when written.
- Very large files (long videos, huge PDFs) may be slow, since everything runs on your device.

## Roadmap

- [ ] DOCX: remove tracked changes and comments
- [ ] MP4: more metadata fields (title, artist, comment)
- [ ] AES-256 PDF support
- [ ] Copy metadata to clipboard

## Contributing

Issues and pull requests are welcome. Because MYRA is a single HTML file by design, changes
are easy to review — there's no build pipeline. If you're reporting a format-parsing bug, a
sample file (with sensitive content stripped) that reproduces it is the most useful thing you
can attach.

## License

MIT — see [`LICENSE`](./LICENSE). Use it, fork it, ship it.

---

<div align="center">

Built with Claude · Your files never leave your browser

</div>
