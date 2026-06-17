## GD Object Placement Visualizer

A spatial debug viewer for **Geometry Dash** custom levels that visualizes the placement of all objects within a level. This tool helps creators analyze object distributions, identify clustering issues, and export placement data for further analysis or custom game engine integration.

---

## 📋 Features

- **Spatial Map Viewer** — Interactive 2D visualization of all placed objects with proper coordinate mapping
- **ID Filtering** — Isolate and highlight specific object types by ID for detailed inspection
- **Interactive Navigation** — Zoom and pan the level map for clarity
- **Coordinate Systems** — Display positions in both **GD Units** (native) and **GD Tiles** (1 tile = 30 GD Units)
- **Object Statistics** — Top 25 most-used object IDs ranked by frequency
- **XML Export** — Export object placement data as structured XML for use in custom engines
- **Multiple Input Formats** — Support for `.gmd`, `.txt`, `.xml`, `.json`, and `.html` files
- **Gzip/Base64 Decoding** — Automatically decompress and decode level strings from save files
- **Alpha Release** — Feature-rich but may have edge cases with extremely dense object placements

---

## 🚀 How to Use

### 1. **Extract Your Level Data**

First, you need to extract the level contents from your Geometry Dash save file:

- Visit **[GDColon Save Editor](https://gdcolon.com/gdsave/)** 
- Upload your save file or paste your level code
- Locate your custom level and extract the level data
- Save the extracted data (typically a `.gmd` file or raw level string)

### 2. **Open the Visualizer**

- Download or clone this repository
- Open `ObjectPlacementMap.html` in your browser (Chrome, Edge, or any modern browser with `DecompressionStream` support)
- An embedded sample level loads automatically

### 3. **Load Your Level**

#### Option A: From a File
- Click **"Import custom level"** and select your extracted level file (`.gmd`, `.txt`, `.xml`, `.json`, or `.html`)
- Click **"Load Level"** button
- The map updates with all objects from your level

#### Option B: From Raw Level String
- If you have a raw decoded level string, paste it directly into a `.txt` file
- Import using the same file picker

### 4. **Navigate and Explore**

| Action | Method |
|--------|--------|
| **Zoom In** | Mouse wheel up, or click "Zoom +" button |
| **Zoom Out** | Mouse wheel down, or click "Zoom -" button |
| **Pan/Move** | Click and drag the map |
| **Reset View** | Click "Reset View" button |
| **View Coordinates** | Hover over the map; GD Units and GD Tiles display at bottom |

### 5. **Filter Objects**

- Enter one or more **object IDs** in the "Show only object ID" field (e.g., `1, 8, 1330`)
- Click **"Apply"** to filter the view
- Click **"Show all"** to display all objects again
- The object count updates to show how many match the filter

### 6. **Export Data**

- Click **"Export XML"** to download an XML file containing all object placement data
- The file includes:
  - Object ID
  - Position (in both GD Units and GD Tiles)
  - Rotation, color, scale, and group data
  - All metadata for custom engine integration

---

## 📊 Understanding the Map

### Coordinate System
- **GD Units** — The native coordinate system used by Geometry Dash (1:1 pixel equivalent)
- **GD Tiles** — Logical grid units where 1 tile = 30 GD Units
- Every object is displayed as a **1×1 GD Tile box** (30 GD Units) for consistent placement visualization, regardless of actual object size

### Grid
- **Minor Grid Lines** — 30 GD Units (1 tile) apart
- **Major Grid Lines** — 300 GD Units (10 tiles) apart
- Grid labels auto-adjust based on zoom level for readability

### Colors
- Each unique object ID gets a **distinct hue** for visual distinction
- Objects are color-coded by type for quick pattern recognition

---

## 🔗 References & Resources

### Essential Tools
- **[GDColon Save Editor](https://gdcolon.com/gdsave/)** — Extract level data from Geometry Dash save files
- **[Geometry Dash Object Database](https://geometry-dash.fandom.com/)** — Object ID reference and properties

### Geometry Dash Documentation
- **Object IDs** — Reference all 600+ object types and their properties
- **Level Format** — Understanding `.gmd` file structure and level string encoding
- **Coordinate System** — GD Units and tile-based positioning

### Related Projects
- Custom game engine implementations using exported XML data
- Level analysis and optimization tools
- Object distribution heatmaps and analytics

---

## ⚠️ Known Limitations & Notes

- **Alpha Release** — This is an early version; edge cases with extremely dense object clusters may cause rendering issues
- **Browser Support** — Requires modern browsers with `DecompressionStream` API (Chrome, Edge, or equivalent). Firefox may require a workaround
- **Zoom Limits** — Very long or tall levels have capped initial zoom for usability; zooming in/out allows full exploration
- **Performance** — Levels with 50,000+ objects may experience lag during interactions
- **Scale Visualization** — Object size scaling is not visually rendered; all objects display as 1×1 tiles for consistency

---

## 🛠️ Technical Notes

### Architecture
- **Single HTML File** — No build step or dependencies required
- **Client-Side Only** — All processing happens in your browser; no data sent to servers
- **Embedded Sample Level** — Includes a pre-loaded level for testing without file import
- **SVG-Based Rendering** — Scalable vector graphics for crisp rendering at any zoom level

### Input Formats Supported
| Format | Example | Notes |
|--------|---------|-------|
| `.gmd` | Geometry Dash save format | Automatically decompressed if gzipped |
| `.txt` | Raw level string | Decoded level data (semicolon-separated) |
| `.xml` | XML export from this tool | Reimport previously exported data |
| `.json` | JSON with `k4` field | Must contain the gzipped base64 level data |
| `.html` | HTML with embedded `<k>k4</k><s>...</s>` | Common export format |

### Level String Format
Objects are represented as semicolon-separated segments with comma-separated key-value pairs:
```
id,1,x_pos,2,y_pos,3,rot,6,color,21|id,1,x_pos,2,y_pos,3,rot,6,color,21|...
```

---

## 📝 Future Enhancements

Potential features for future releases:
- Heatmap visualization showing object density
- Layer filtering (editor layer support)
- Group highlighting and analysis
- Performance optimization for massive levels
- Mobile touch controls refinement
- Angle/rotation visualization overlay

---

## 📧 Support & Feedback

For issues, questions, or suggestions:
- Open an issue on this repository
- Reference the GDColon Save Editor for level extraction questions
- Check browser console for detailed error messages

---

**Happy level designing! 🎮**
