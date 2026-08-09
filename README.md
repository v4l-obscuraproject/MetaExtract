# MetaExtract

**MetaExtract** pulls hidden metadata out of files — the stuff that
doesn't show up when you just open and read a document, but is sitting
in its underlying structure. Written in **Python 3**, **MIT-licensed**.

## Installation and Running

MetaExtract requires Python 3.8+ and a few external libraries.

### macOS / Linux

```bash
git clone https://github.com/v4l-obscuraproject/MetaExtract
cd MetaExtract
pip3 install pypdf pillow python-docx openpyxl
python3 meta_extract.py yourfile.pdf
```

### Windows

```
git clone https://github.com/v4l-obscuraproject/MetaExtract
cd MetaExtract
pip install pypdf pillow python-docx openpyxl
python meta_extract.py yourfile.pdf
```

### macOS security warning

macOS may show an "unsafe" / "can't be opened because it is from an
unidentified developer" warning when running downloaded scripts for the
first time. This is standard Gatekeeper behavior for any file downloaded
from the internet, not a sign of an actual problem with this specific
file. If you've reviewed the code and trust it, allow it via:

**System Settings → Privacy & Security → scroll down → "Open Anyway"**

### Windows security warning

Windows Defender SmartScreen may show a "Windows protected your PC"
warning the first time you run a downloaded script. This is standard
SmartScreen behavior, not a sign of a problem with this file. If you've
reviewed the code and trust it, proceed via:

**Click "More info" → "Run anyway"**

## What it extracts

| File type | Metadata pulled |
|---|---|
| PDF (`.pdf`) | Author, creation/modification date, software used, title, subject, page count |
| Images (`.jpg`, `.jpeg`, `.png`) | Format, dimensions, camera/software info, GPS coordinates (if present) |
| Word docs (`.docx`) | Author, last modified by, company, created/modified dates, revision number |
| Excel files (`.xlsx`) | Author, last modified by, company, created/modified dates |

## Usage

```bash
python3 meta_extract.py path/to/file.pdf
python3 meta_extract.py path/to/photo.jpg
python3 meta_extract.py path/to/document.docx
```

## Why this matters

Files often carry metadata their creator never realized was there — a
real name in a PDF's author field, the exact software and version used
to create a document, or GPS coordinates embedded in a photo. This is a
standard technique in real OSINT and digital forensics work: it's how
document leaks sometimes get traced back to a source, and how
organizations discover they've been leaking internal details (usernames,
software versions, file paths) through publicly posted files without
realizing it.

**Pairs naturally with [DorkRecon](https://github.com/v4l-obscuraproject/DorkRecon):**
DorkRecon finds publicly indexed files on a domain (its "Publicly
indexed documents" dork category). MetaExtract then reveals what's
hidden inside those files once you've downloaded them.

## Intended use case

Reviewing files you own or have authorization to analyze, as part of a
security assessment — checking whether your organization's public
documents are unintentionally leaking author names, software versions,
or location data. Also useful for general digital forensics learning.

**Not intended for:** identifying or tracking a specific person without
authorization. Extracting a file's metadata doesn't require the file
owner's permission technically, but using the results to target or
locate a specific individual is not an acceptable use of this tool.

## License

MIT License — see [LICENSE](LICENSE) for details.

## Credits

Made by **5h9q_** (developer) 
See [CREDITS.md](CREDITS.md).