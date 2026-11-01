# 🦉 MYRA — My Redact Assistant

A personal tool for viewing, editing and removing hidden metadata in files. It runs entirely in
the browser from a single `index.html` — no backend, no accounts, nothing is uploaded.

[**MYRA live →**](https://saicharan-adakankar.github.io/myra/)

## What it can do

- **Read** the hidden metadata in a file and group it into Identity, Origin, Timeline, Content and Security.
- **Edit** any metadata field, and **add** fields the file doesn't have yet.
- **Remove** individual fields, with undo before export.
- **Unlock** password-protected PDFs, and **set a password** on a PDF at export.
- **Preview** the file (image, video frame, PDF page, document text).
- **Export** a copy with the same file name. The original is never modified.
- Dark (AMOLED) and light themes; works on desktop and mobile.

## Supported formats

| Format | Editable metadata |
|---|---|
| JPG | Author, copyright, camera make/model, software, dates; remove GPS and thumbnail |
| PNG | Title, author, copyright, description, comment, software, source, creation time |
| PDF | Title, author, subject, creator, producer, keywords, dates; password unlock / protect |
| DOCX | Title, author, last modified by, company, application, template, dates |
| MP4 | Created and modified dates |

## What it's built with

- **Plain HTML, CSS and JavaScript** in one file — no framework, no build step.
- **piexifjs** — JPEG EXIF read/write
- **pdf-lib** — PDF metadata read/write
- **pdf.js** — PDF rendering and opening protected PDFs
- **JSZip** — DOCX (zip) read/write
- Written by hand, no library: PNG chunk parsing, MP4 header patching, and PDF password
  handling (RC4-128 per the PDF spec).

## How it was developed

Designed and built iteratively with Claude (Anthropic): a data-driven architecture where each
format parser returns a common list of fields, and the same Overview, Editor and export code
works for every format. Format-specific write-back logic lives with each parser.

## Known limits

- PDF export password uses RC4-128; AES-256 PDFs can be viewed but not unlocked for editing.
- DOCX tracked changes and comments are shown but not removable.
- MP4 editing covers only the Created/Modified timestamps.
- Very large files may be slow, since everything runs on the local device.
