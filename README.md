# sd-zonecreator

> A visual zone creation tool for FiveM featuring an interactive map interface, real-time 3D preview, and multiple export formats.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0f598d45-72ba-4e18-9af7-efec27adbcaa" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ed58c11c-716d-44ee-aaac-eef6ed02a5fa" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/96b95e76-37f7-4d79-a3b4-a1af3464c160" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5d4f929b-e29a-463b-b514-51474315d8a2" />


![GitHub release](https://img.shields.io/github/v/release/Samuels-Development/sd-zonecreator?label=Release&logo=github)
[![Discord](https://img.shields.io/discord/842045164951437383?label=Discord&logo=discord&logoColor=white)](https://discord.gg/FzPehMQaBQ)

## 📋 Dependencies

- [ox_lib](https://github.com/overextended/ox_lib)

## 🎯 Features

### Core Features

- **Interactive Map** - Click to place zone points on a high-resolution GTA V satellite map
- **Real-time 3D Preview** - View your zone in-game with a free-fly camera system
- **Multiple Export Formats** - Export to PolyZone, ox_lib, vector2, or vector3 formats
- **Import Support** - Paste existing zone code to edit and visualize zones
- **Auto Ground Z** - Automatically calculates ground height at the zone center
- **Multi-Zone Management** - Create and manage multiple zones in a single session

### Template Shapes

Quickly create zones using pre-built shape templates:

| Shape | Description |
|-------|-------------|
| **Rectangle** | 4-point square/rectangular zone |
| **Circle** | 16-point circular approximation |
| **Triangle** | 3-point triangular zone |
| **Pentagon** | 5-point pentagonal zone |
| **Hexagon** | 6-point hexagonal zone |
| **Star** | 10-point star shape |
| **L-Shape** | 6-point L-shaped zone |

All templates support:
- **Drag to Position** - Drag the center marker to reposition the shape
- **Scale Slider** - Adjust the size from 5 to 3000 units
- **Rotation Slider** - Rotate the shape from 0° to 360°

### Point Management

- **Click on Map** - Add a new point to the active zone
- **Drag Points** - Click and drag any point marker to reposition it
- **Right-click Point** - Delete a single point
- **Click on Polygon Edge** - Insert a new point on the closest edge
- **Shift + Drag** - Box select multiple points
- **Delete Selected** - Remove all selected points at once

### Zone Settings

Each zone has configurable properties:

| Setting | Description |
|---------|-------------|
| **Name** | Zone identifier (click pencil icon to rename) |
| **Color** | Automatic color assignment (8 colors cycle) |
| **Visibility** | Toggle zone display on/off |
| **Ground Z** | Base height of the zone (auto-calculate or manual) |
| **Thickness** | Vertical height of the zone |

### Map Tools

| Tool | Shortcut | Description |
|------|----------|-------------|
| **Snap to Grid** | `G` | Snap points to 10-unit grid (shows grid overlay) |
| **Show Distances** | `D` | Display distance labels between adjacent points |
| **Undo** | `Ctrl+Z` | Undo last action |
| **Redo** | `Ctrl+Y` | Redo last undone action |
| **Search Location** | `Ctrl+F` | Jump to specific X, Y coordinates |
| **Jump to Player** | Button | Center map on your current position |

### Additional Features

- **Zoom Controls** - Mouse wheel or +/- buttons to zoom (displays zoom percentage)
- **Coordinate Display** - Real-time cursor coordinates shown at bottom of map
- **Player Marker** - Shows your in-game position on the map
- **Active Zone Indicator** - Visual indicator showing which zone you're editing
- **Point Tooltips** - Hover over points to see their exact coordinates
- **Notifications** - Toast notifications for actions (copy, create, delete, etc.)

---

## 📦 Installation

1. [Download the latest release](https://github.com/Samuels-Development/sd-zonecreator/releases/latest) (ZIP, NOT SOURCE)
2. Ensure `ox_lib` is started before `sd-zonecreator`
3. Add `sd-zonecreator` to your resources folder
4. Add `ensure sd-zonecreator` to your server.cfg

---

## 🛠️ Usage

### Opening the Zone Creator

Use the command to open the zone creator interface:

```
/zonecreator
```

### Creating a Zone

1. Click on the map to place zone points
2. Add at least 3 points to form a polygon
3. Adjust the zone name, thickness, and ground Z as needed
4. Use "View Zone" to preview your zone in-game with a 3D camera

### Exporting Zones

Click any of the export buttons to copy the zone data to your clipboard:

| Format | Description |
|--------|-------------|
| **PolyZone** | Full PolyZone.Create code with all parameters |
| **ox_lib** | Full lib.zones.poly code for ox_lib |
| **vec2** | List of vector2 coordinates (x, y) |
| **vec3** | List of vector3 coordinates (x, y, z) |

### Importing Zones

1. Click the "Import" tab
2. Paste existing zone code (supports PolyZone, ox_lib, or vector formats)
3. Click "Import Zone" to load the zone for editing

### Zone Viewer Controls

When viewing a zone in 3D:

| Control | Action |
|---------|--------|
| **W A S D** | Move camera horizontally |
| **Q / E** | Move camera up / down |
| **Mouse** | Look around |
| **Shift** | Sprint (faster movement) |
| **Arrow Up / Down** | Adjust zone thickness |
| **Backspace** | Exit viewer and return to map |

---

## 🎨 Export Examples

### PolyZone Output

```lua
local myZone = PolyZone:Create({
    vector2(100.0, 200.0),
    vector2(150.0, 200.0),
    vector2(150.0, 250.0),
    vector2(100.0, 250.0),
}, {
    name = "myZone",
    minZ = 25.0,
    maxZ = 175.0,
})
```

### ox_lib Output

```lua
local myZone = lib.zones.poly({
    name = "myZone",
    points = {
        vec3(100.0, 200.0, 30.0),
        vec3(150.0, 200.0, 30.0),
        vec3(150.0, 250.0, 30.0),
        vec3(100.0, 250.0, 30.0),
    },
    thickness = 150,
    onEnter = function(self)
        print('Entered', self.name)
    end,
    onExit = function(self)
        print('Exited', self.name)
    end,
})
```

### vector2 Output

```lua
vector2(100.0, 200.0),
vector2(150.0, 200.0),
vector2(150.0, 250.0),
vector2(100.0, 250.0),
```

### vector3 Output

```lua
vector3(100.0, 200.0, 30.0),
vector3(150.0, 200.0, 30.0),
vector3(150.0, 250.0, 30.0),
vector3(100.0, 250.0, 30.0),
```

---

## ⌨️ Keyboard Shortcuts Quick Reference

### Map Editor

| Shortcut | Action |
|----------|--------|
| `G` | Toggle snap to grid |
| `D` | Toggle distance labels |
| `Ctrl+Z` | Undo |
| `Ctrl+Y` or `Ctrl+Shift+Z` | Redo |
| `Ctrl+F` | Open search/jump to location |
| `Delete` or `Backspace` | Delete last point from active zone |
| `Escape` | Close zone creator |

### Zone Viewer (3D Preview)

| Shortcut | Action |
|----------|--------|
| `W` `A` `S` `D` | Move camera |
| `Q` / `E` | Move up / down |
| `Shift` | Sprint |
| `Arrow Up` / `Arrow Down` | Adjust thickness |
| `Backspace` | Exit viewer |

---
