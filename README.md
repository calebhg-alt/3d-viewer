# AVC 3D Model Viewer

An accessible, browser-based 3D model viewer built for **Antelope Valley College** CTE Welding students. Hosted on GitHub Pages and embedded in Canvas via iframe.

**Live URL:** `https://calebhg-alt.github.io/3d-viewer/3d-viewer.html`

---

## Features

- Supports **STL, GLB, GLTF, and OBJ** file formats
- Per-model **access codes** — students must enter a code to unlock each model
- **Instructor panel** locked behind PIN `7018`
- On-screen **D-pad controls** for rotate, pan, zoom, and views
- **Keyboard shortcuts** (after clicking the viewer to activate)
- **Linear and radial measurement** tools with vertex snapping
- **6 view presets** — Front, Back, Right, Left, Top, Bottom
- Wireframe toggle
- WCAG 2.1 AA accessible
- AVC branded header

---

## How to Add a New Model

### Step 1 — Upload the file to GitHub

1. Go to `github.com/calebhg-alt/3d-viewer`
2. Click into the **`models/`** folder
3. Click **Add file → Upload files**
4. Drag your `.stl`, `.glb`, or `.obj` file in
5. Click **Commit changes**

### Step 2 — Register the model in the viewer

1. Go back to the repo root and click `3d-viewer.html`
2. Click the **pencil icon** to edit
3. Find the `MODELS` array near the top of the `<script>` tag:

```javascript
const MODELS=[
  {label:'Bracket 1', url:'models/obj%202.stl', code:'ALPHA-101'},
  ...
];
```

4. Add a new line for your model:

```javascript
{label:'My New Part', url:'models/yourfile.stl', code:'MYCODE-001'},
```

5. Click **Commit changes**

> **Note:** If your filename contains spaces, encode them as `%20`.  
> Example: `my part.stl` → `models/my%20part.stl`

---

## Filename Encoding Reference

| Filename on disk | URL in MODELS list |
|---|---|
| `bracket.stl` | `models/bracket.stl` |
| `obj 2.stl` | `models/obj%202.stl` |
| `my part v2.glb` | `models/my%20part%20v2.glb` |

---

## Supported File Formats

| Format | Extension | Notes |
|---|---|---|
| StereoLithography | `.stl` | Binary and ASCII supported |
| GL Transmission Format | `.glb` `.gltf` | Preserves materials and color |
| Wavefront OBJ | `.obj` | Renders in default gray material |

> **SolidWorks `.sldprt` files are not supported** in the browser.  
> Convert to `.stl` or `.glb` first using FreeCAD (free) or SolidWorks Save As.

---

## Keyboard Shortcuts

> Click anywhere on the viewer first to activate keyboard controls.

| Key | Action |
|---|---|
| `←` `→` `↑` `↓` | Rotate |
| `Shift` + arrows | Pan |
| `+` / `-` | Zoom in / out |
| `1` | Front view |
| `2` | Back view |
| `3` | Right view |
| `4` | Left view |
| `5` | Top view |
| `6` | Bottom view |
| `R` | Reset camera |
| `L` | Linear measure |
| `C` | Radial measure |
| `W` | Toggle wireframe |
| `Esc` | Cancel current action |

---

## Embedding in Canvas

Paste this into the Canvas page HTML editor (`< >` button):

```html
<iframe
  src="https://calebhg-alt.github.io/3d-viewer/3d-viewer.html"
  width="100%"
  height="900px"
  allowfullscreen
  style="border:none;">
</iframe>
```

> If the viewer appears blank in Canvas, ask your Canvas admin to add `github.io` to the approved iframe domains under **Admin → Security → Allowed Domains**.

---

## Model Access Codes

Access codes are set in the `MODELS` array inside `3d-viewer.html`.  
The instructor panel (PIN: `7018`) shows all codes and unlock status.

---

## Instructor PIN

The instructor panel is protected by PIN **`7018`**.  
To change it, edit this line near the top of the script in `3d-viewer.html`:

```javascript
const INSTRUCTOR_PIN='7018';
```

---

## Folder Structure

```
3d-viewer/
├── 3d-viewer.html        ← Main viewer file
├── README.md             ← This file
└── models/
    ├── obj 2.stl         ← Bracket 1
    ├── model-02.stl      ← Placeholder
    └── ...               ← Add your models here
```

---

## Credits

**Created by:** Caleb Healey  
**Department:** CTE Welding, Antelope Valley College  
**Course:** WELD 260
