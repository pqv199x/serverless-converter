# 📚 Ultimate Local Converter

> A **100% serverless, privacy-first** document & comic converter that runs entirely in your browser.
> No uploads. No servers. No installations. Just drag, drop, and convert.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![Privacy](https://img.shields.io/badge/Privacy-100%25%20Local-brightgreen)

---

## ✨ Features

- 🔒 **100% Private** — Files never leave your device. Zero network calls during conversion.
- 🚀 **Zero Setup** — No Node.js, no `npm install`, no backend. Just open an HTML file.
- 📱 **Fully Responsive** — Works beautifully on phones, tablets, and desktops.
- 🎨 **Quality Control** — Adjustable JPEG quality slider (10%–100%).
- 📦 **Multiple Outputs** — Export to **PDF** or **ZIP of images**.
- ⚡ **Smart Processing** — Auto EXIF rotation, natural page sorting, and dynamic document rendering.

---

## 🚀 Quick Start

1. Download or save the `converter.html` file to your computer.
2. **Double-click** the file to open it in any modern browser (Chrome, Edge, Firefox, Safari).
3. Drag & drop your file, adjust settings, and click **Convert**.

That's it. No server, no dependencies, no tracking.

---

## 📂 Supported Formats

### ✅ Input Formats

| Category | Formats |
|----------|---------|
| 📖 **Comics & Manga** | `CBZ`, `CBS`, `CBR` |
| 📚 **eBooks** | `EPUB` |
| 📝 **Documents** | `DOCX`, `TXT` |
| 📊 **Spreadsheets** | `XLSX`, `CSV` |
| 🖼️ **Images** | `TIFF`, `TIF` |

### ⚠️ Limited Support

| Format | Status |
|--------|--------|
| `MOBI`, `AZW3` | ⚠️ Proprietary Amazon formats. The tool will warn you and suggest using [Calibre](https://calibre-ebook.com/) to convert them to EPUB first. |

### 🎯 Output Formats

- **PDF Document** — Perfectly paginated, high-quality PDF.
- **Images (ZIP Archive)** — Extracted pages as individual JPEG files.

---

## 🛠️ How It Works

Everything runs **client-side** using powerful JavaScript and WebAssembly libraries loaded via CDN:

| Library | Purpose |
|---------|---------|
| [JSZip](https://stuk.github.io/jszip/) | Extracts ZIP-based archives (CBZ, EPUB, DOCX, XLSX) |
| [node-unrar-js](https://github.com/YurySolovyov/node-unrar-js) | WebAssembly RAR extractor for CBR files |
| [pdf-lib](https://pdf-lib.js.org/) | Generates the final PDF documents |
| [html2canvas](https://html2canvas.hertzen.com/) | Renders HTML/text documents into images |
| [Mammoth.js](https://github.com/mwilliamson/mammoth.js) | Converts DOCX to clean HTML |
| [SheetJS](https://sheetjs.com/) | Reads XLSX/CSV spreadsheets |
| [UTIF.js](https://github.com/photopea/UTIF.js) | Decodes complex TIFF images |

### The Conversion Pipeline

```text
File → Extract → Normalize → Render → Export
  │         │          │          │         │
  │    JSZip/UnRAR   Canvas    html2canvas  pdf-lib
  │    UTIF.js       (EXIF fix)            or JSZip