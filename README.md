## GD Object Placement Visualizer

A spatial debug viewer for **Geometry Dash** custom level data that visualizes object placement across a full 2D map.

This tool now supports both:
1. **Direct level imports** (`.gmd`, raw strings, etc.), and  
2. **Created Levels save parsing** from `CCLocalLevels.dat` / `.xml` / `.plist`, with one-click loading into the map.

---

## 📋 Features

### Core Visualizer
- **Interactive 2D Placement Map** — Displays all placed objects with proper coordinate mapping
- **Object ID Filtering** — Isolate one or more IDs (example: `1, 8, 1330`)
- **Zoom + Pan Navigation** — Mouse wheel zoom, drag pan, and reset controls
- **Dual Coordinates**:
  - **GD Units** (native)
  - **GD Tiles** (`1 tile = 30 GD Units`)
- **Top Object Statistics** — Top 25 most-used IDs by frequency
- **XML Export** — Export object placement + metadata for engine/tool pipelines
- **Auto Decode Support** — Handles base64 + gzip level data when applicable
- **Embedded Sample Level** — Quick load for testing

### New: Created Levels Save Browser
- **Import Created Levels Files**:
  - `CCLocalLevels.dat`
  - `.xml`
  - `.plist`
  - `.txt` (when compatible save XML/text content is present)
- **Parses Local Created Levels (`LLM_01`)** from Geometry Dash save structure
- **Search + Sortable Levels Table** with columns like:
  - Name / Description
  - Object Count
  - Editor Time
  - Level ID / Copied ID
  - Attempts / Jumps / Song ID
  - Folder / Revision / Local Version / Save Key
  - Compressed size
- **View Level Action** — Load any listed created level directly into the object placement map

---

## 🚀 How to Use

## 1) Open the tool
- Clone/download this repository
- Open `ObjectPlacementMap.html` in a modern browser (Chrome/Edge recommended)

## 2) Load a level (two options)

### Option A — Direct level import
Use **Import custom level** for:
- `.gmd`, `.txt`, `.xml`, `.json`, `.html`

Then click **Load Level**.

### Option B — Created Levels import (new)
Use **Import saved levels** for:
- `CCLocalLevels.dat`, `.xml`, `.plist`, `.txt`

Then click **Load Saved Levels**.

After parsing:
- Browse the **Created Levels** table
- Search and sort entries
- Click **View Level** on any row to render it in the map

---

## 🧭 Map Controls

| Action | Method |
|---|---|
| Zoom In | Mouse wheel up or **Zoom +** |
| Zoom Out | Mouse wheel down or **Zoom -** |
| Pan | Click + drag |
| Reset | **Reset View** |
| Filter IDs | Enter IDs and click **Apply** |
| Clear Filter | **Show all** |
| Export XML | **Export XML** |

---

## 📊 Coordinate + Grid Notes

- **GD Units** are Geometry Dash native coordinates.
- **GD Tiles** are logical tiles where `1 tile = 30 GD Units`.
- Objects are shown as **1×1 tile debug boxes** for consistent placement analysis.
- Grid:
  - Minor lines: every **30 units**
  - Major lines: every **300 units**
- Grid labels adapt to zoom level.

---

## 📁 Supported Inputs

### Level Map Import
| Format | Purpose |
|---|---|
| `.gmd` | Geometry Dash level data |
| `.txt` | Raw decoded level string |
| `.xml` | XML-compatible level source |
| `.json` | Level payload (e.g., containing `k4`) |
| `.html` | Embedded save-like content (`k4`) |

### Created Levels Import
| Format | Purpose |
|---|---|
| `CCLocalLevels.dat` | Main local created-levels save file |
| `.xml` / `.plist` | Decrypted/converted save structures |
| `.txt` | Compatible textual save export |

---

## 🛠️ Technical Notes

- **Single-file app** (`ObjectPlacementMap.html`)
- **No build step / no external dependencies**
- **Browser-only processing** (local; no server upload required)
- Uses browser decompression APIs (`DecompressionStream`) when needed
- Includes decoding paths for common Geometry Dash save encodings used in local level data

---

## ⚠️ Limitations

- Very large levels (50k+ objects) may lag during interaction
- Some edge-case save variants may fail to decode
- Firefox may require alternative workflows depending on decompression API support
- Visualized boxes are normalized for placement clarity (not full sprite-size rendering)

---

## 🔗 Helpful Resources

- [GDColon Save Editor](https://gdcolon.com/gdsave/) — Save extraction/conversion helper
- [Geometry Dash Object Reference (Fandom)](https://geometry-dash.fandom.com/) — Object IDs and info

---

## 📝 Feedback

If you find an issue or want to suggest features:
- Open an issue in this repository
- Include:
  - File type used (`.dat`, `.xml`, `.gmd`, etc.)
  - Browser/version
  - Console error output (if available)
