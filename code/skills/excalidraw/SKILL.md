---
name: draw-excalidraw-image
description: Use this skill when you need to create diagrams, flowcharts, data flow visualizations, or any visual documentation in Excalidraw format. This skill provides the complete specification for generating valid .excalidraw JSON files that can be opened in VS Code (with Excalidraw extension) or excalidraw.com.
---

# Excalidraw Diagram Generation Skill

## Overview

This skill enables you to create professional diagrams by generating valid `.excalidraw` JSON files. Use this for:
- Data flow diagrams
- System architecture diagrams
- Flowcharts
- Entity relationship diagrams
- Sequence diagrams (simplified)
- Any visual documentation

## File Structure

Every `.excalidraw` file must follow this structure:

```json
{
  "type": "excalidraw",
  "version": 2,
  "source": "https://claude.ai/claude-code",
  "elements": [],
  "appState": {
    "gridSize": 20,
    "gridStep": 5,
    "gridModeEnabled": false,
    "viewBackgroundColor": "#ffffff"
  },
  "files": {}
}
```

## Element Types

### 1. Rectangle (矩形)

Use for: Process nodes, data stores, components, containers

```json
{
  "type": "rectangle",
  "id": "rect-unique-id",
  "x": 100,
  "y": 100,
  "width": 180,
  "height": 70,
  "angle": 0,
  "strokeColor": "#1e1e1e",
  "backgroundColor": "#a5d8ff",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 1,
  "opacity": 100,
  "groupIds": [],
  "frameId": null,
  "index": "a0",
  "roundness": { "type": 3 },
  "seed": 1733100000001,
  "version": 1,
  "versionNonce": 1733100000001,
  "isDeleted": false,
  "boundElements": [],
  "updated": 1733100000000,
  "link": null,
  "locked": false
}
```

### 2. Text (文本)

Use for: Labels inside shapes, standalone annotations

**Bound text (inside a shape):**
```json
{
  "type": "text",
  "id": "text-unique-id",
  "x": 110,
  "y": 120,
  "width": 160,
  "height": 30,
  "angle": 0,
  "strokeColor": "#1e1e1e",
  "backgroundColor": "transparent",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 1,
  "opacity": 100,
  "groupIds": [],
  "frameId": null,
  "index": "a1",
  "roundness": null,
  "seed": 1733100000002,
  "version": 1,
  "versionNonce": 1733100000002,
  "isDeleted": false,
  "boundElements": null,
  "updated": 1733100000000,
  "link": null,
  "locked": false,
  "text": "Label Text",
  "fontSize": 16,
  "fontFamily": 1,
  "textAlign": "center",
  "verticalAlign": "middle",
  "containerId": "rect-unique-id",
  "originalText": "Label Text",
  "autoResize": true,
  "lineHeight": 1.25
}
```

**Standalone text:**
```json
{
  "type": "text",
  "id": "text-standalone-id",
  "x": 100,
  "y": 50,
  "width": 200,
  "height": 25,
  "angle": 0,
  "strokeColor": "#1e1e1e",
  "backgroundColor": "transparent",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 1,
  "opacity": 100,
  "groupIds": [],
  "frameId": null,
  "index": "a2",
  "roundness": null,
  "seed": 1733100000003,
  "version": 1,
  "versionNonce": 1733100000003,
  "isDeleted": false,
  "boundElements": null,
  "updated": 1733100000000,
  "link": null,
  "locked": false,
  "text": "Diagram Title",
  "fontSize": 20,
  "fontFamily": 1,
  "textAlign": "left",
  "verticalAlign": "top",
  "containerId": null,
  "originalText": "Diagram Title",
  "autoResize": true,
  "lineHeight": 1.25
}
```

### 3. Arrow (箭头)

Use for: Data flow, connections, relationships

**Simple arrow (unbound):**
```json
{
  "type": "arrow",
  "id": "arrow-unique-id",
  "x": 280,
  "y": 135,
  "width": 100,
  "height": 0,
  "angle": 0,
  "strokeColor": "#1e1e1e",
  "backgroundColor": "transparent",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 1,
  "opacity": 100,
  "groupIds": [],
  "frameId": null,
  "index": "a3",
  "roundness": { "type": 2 },
  "seed": 1733100000004,
  "version": 1,
  "versionNonce": 1733100000004,
  "isDeleted": false,
  "boundElements": null,
  "updated": 1733100000000,
  "link": null,
  "locked": false,
  "points": [[0, 0], [100, 0]],
  "lastCommittedPoint": null,
  "startBinding": null,
  "endBinding": null,
  "startArrowhead": null,
  "endArrowhead": "arrow",
  "elbowed": false
}
```

**Bound arrow (connects two shapes):**
```json
{
  "type": "arrow",
  "id": "arrow-bound-id",
  "x": 280,
  "y": 135,
  "width": 100,
  "height": 0,
  "angle": 0,
  "strokeColor": "#1e1e1e",
  "backgroundColor": "transparent",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 1,
  "opacity": 100,
  "groupIds": [],
  "frameId": null,
  "index": "a4",
  "roundness": { "type": 2 },
  "seed": 1733100000005,
  "version": 1,
  "versionNonce": 1733100000005,
  "isDeleted": false,
  "boundElements": null,
  "updated": 1733100000000,
  "link": null,
  "locked": false,
  "points": [[0, 0], [100, 0]],
  "lastCommittedPoint": null,
  "startBinding": {
    "elementId": "source-shape-id",
    "focus": 0,
    "gap": 1,
    "fixedPoint": null
  },
  "endBinding": {
    "elementId": "target-shape-id",
    "focus": 0,
    "gap": 1,
    "fixedPoint": null
  },
  "startArrowhead": null,
  "endArrowhead": "arrow",
  "elbowed": false
}
```

**Arrow with label:** Create a separate text element near the arrow's midpoint.

### 4. Diamond (菱形)

Use for: Decision points, conditions

```json
{
  "type": "diamond",
  "id": "diamond-unique-id",
  "x": 100,
  "y": 200,
  "width": 120,
  "height": 80,
  "angle": 0,
  "strokeColor": "#1e1e1e",
  "backgroundColor": "#ffec99",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 1,
  "opacity": 100,
  "groupIds": [],
  "frameId": null,
  "index": "a5",
  "roundness": { "type": 2 },
  "seed": 1733100000006,
  "version": 1,
  "versionNonce": 1733100000006,
  "isDeleted": false,
  "boundElements": [],
  "updated": 1733100000000,
  "link": null,
  "locked": false
}
```

### 5. Ellipse (椭圆)

Use for: Start/end points, external systems, APIs

```json
{
  "type": "ellipse",
  "id": "ellipse-unique-id",
  "x": 100,
  "y": 100,
  "width": 140,
  "height": 70,
  "angle": 0,
  "strokeColor": "#1e1e1e",
  "backgroundColor": "#b2f2bb",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 1,
  "opacity": 100,
  "groupIds": [],
  "frameId": null,
  "index": "a6",
  "roundness": { "type": 2 },
  "seed": 1733100000007,
  "version": 1,
  "versionNonce": 1733100000007,
  "isDeleted": false,
  "boundElements": [],
  "updated": 1733100000000,
  "link": null,
  "locked": false
}
```

### 6. Line (直线)

Use for: Simple connections without arrows, separators

```json
{
  "type": "line",
  "id": "line-unique-id",
  "x": 100,
  "y": 300,
  "width": 200,
  "height": 0,
  "angle": 0,
  "strokeColor": "#1e1e1e",
  "backgroundColor": "transparent",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 1,
  "opacity": 100,
  "groupIds": [],
  "frameId": null,
  "index": "a7",
  "roundness": { "type": 2 },
  "seed": 1733100000008,
  "version": 1,
  "versionNonce": 1733100000008,
  "isDeleted": false,
  "boundElements": null,
  "updated": 1733100000000,
  "link": null,
  "locked": false,
  "points": [[0, 0], [200, 0]],
  "lastCommittedPoint": null,
  "startBinding": null,
  "endBinding": null,
  "startArrowhead": null,
  "endArrowhead": null
}
```

## Color Palette

### Semantic Colors (by node type)

| Purpose | Background | Stroke | Usage |
|---------|------------|--------|-------|
| API/Data Source | `#a5d8ff` | `#1971c2` | External APIs, databases, inputs |
| Function/Process | `#d0bfff` | `#7048e8` | Functions, transformations, processing |
| Component/Consumer | `#b2f2bb` | `#2f9e44` | UI components, consumers, outputs |
| Decision Point | `#ffec99` | `#f08c00` | Conditions, branches, if/else |
| Data Store/State | `#ffc9c9` | `#e03131` | State management, cache, storage |
| External System | `#e9ecef` | `#495057` | Third-party services, external systems |
| Highlight/Important | `#ffd8a8` | `#e8590c` | Key nodes, warnings |
| Success/Complete | `#b2f2bb` | `#2f9e44` | Success states, completed flows |
| Error/Warning | `#ffc9c9` | `#e03131` | Error paths, failure states |

### Neutral Colors

| Color | Hex | Usage |
|-------|-----|-------|
| Black | `#1e1e1e` | Default stroke, text |
| Dark Gray | `#495057` | Secondary text |
| Light Gray | `#e9ecef` | Backgrounds, disabled |
| White | `#ffffff` | Canvas background |
| Transparent | `transparent` | No fill |

## Layout Guidelines

### Spacing

```
Standard horizontal gap: 120px
Standard vertical gap: 100px
Minimum gap between nodes: 80px
```

### Node Dimensions

| Element | Width | Height |
|---------|-------|--------|
| Standard Rectangle | 180 | 70 |
| Small Rectangle | 140 | 50 |
| Large Rectangle | 220 | 90 |
| Diamond | 120 | 80 |
| Ellipse | 140 | 70 |
| Small Ellipse | 100 | 50 |

### Flow Directions

- **Top to Bottom**: Default for flowcharts, process diagrams
- **Left to Right**: Data flow diagrams, pipelines
- **Centered**: Star topology, hub-spoke patterns

### Starting Position

Always start the first element at `x: 100, y: 100` to ensure padding from canvas edge.

## Binding Elements

### Text to Shape Binding

When adding text inside a shape:

1. Add `containerId` to text element pointing to shape's ID
2. Add text element reference to shape's `boundElements` array

**Shape with bound text:**
```json
{
  "type": "rectangle",
  "id": "rect-1",
  "boundElements": [
    { "id": "text-1", "type": "text" }
  ]
}
```

**Text bound to shape:**
```json
{
  "type": "text",
  "id": "text-1",
  "containerId": "rect-1",
  "textAlign": "center",
  "verticalAlign": "middle"
}
```

### Arrow to Shape Binding

When connecting shapes with arrows:

1. Add arrow reference to source shape's `boundElements`
2. Add arrow reference to target shape's `boundElements`
3. Set `startBinding` and `endBinding` on arrow

**Source shape:**
```json
{
  "type": "rectangle",
  "id": "source-1",
  "boundElements": [
    { "id": "arrow-1", "type": "arrow" }
  ]
}
```

**Target shape:**
```json
{
  "type": "rectangle",
  "id": "target-1",
  "boundElements": [
    { "id": "arrow-1", "type": "arrow" }
  ]
}
```

**Arrow:**
```json
{
  "type": "arrow",
  "id": "arrow-1",
  "startBinding": { "elementId": "source-1", "focus": 0, "gap": 1, "fixedPoint": null },
  "endBinding": { "elementId": "target-1", "focus": 0, "gap": 1, "fixedPoint": null }
}
```

## ID and Seed Generation

### ID Format

Use descriptive, unique IDs:
- Rectangles: `rect-{name}-{index}` (e.g., `rect-api-1`, `rect-component-2`)
- Text: `text-{parent}-{index}` (e.g., `text-api-1`, `text-title-0`)
- Arrows: `arrow-{source}-{target}` (e.g., `arrow-api-component`)
- Diamonds: `diamond-{name}-{index}` (e.g., `diamond-condition-1`)
- Ellipses: `ellipse-{name}-{index}` (e.g., `ellipse-start-1`)

### Seed and VersionNonce

Use timestamp-based values for uniqueness:
```javascript
const timestamp = Date.now(); // e.g., 1733100000000
seed: timestamp + elementIndex
versionNonce: timestamp + elementIndex
```

### Index Generation

Use alphanumeric index sequence: `a0`, `a1`, `a2`, ... `a9`, `aA`, `aB`, ...

## Arrow Points Calculation

### Horizontal Arrow (Left to Right)
```json
"x": sourceX + sourceWidth,  // Start at right edge of source
"y": sourceY + sourceHeight/2,  // Vertically centered
"points": [[0, 0], [gap, 0]]  // gap = targetX - (sourceX + sourceWidth)
```

### Vertical Arrow (Top to Bottom)
```json
"x": sourceX + sourceWidth/2,  // Horizontally centered
"y": sourceY + sourceHeight,  // Start at bottom edge
"points": [[0, 0], [0, gap]]  // gap = targetY - (sourceY + sourceHeight)
```

### Diagonal Arrow
```json
"x": sourceX + sourceWidth,
"y": sourceY + sourceHeight/2,
"points": [[0, 0], [deltaX, deltaY]]
```

## Complete Example: Simple Data Flow

```json
{
  "type": "excalidraw",
  "version": 2,
  "source": "https://claude.ai/claude-code",
  "elements": [
    {
      "type": "ellipse",
      "id": "ellipse-api-1",
      "x": 100,
      "y": 100,
      "width": 140,
      "height": 70,
      "strokeColor": "#1971c2",
      "backgroundColor": "#a5d8ff",
      "fillStyle": "solid",
      "strokeWidth": 2,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "angle": 0,
      "groupIds": [],
      "frameId": null,
      "index": "a0",
      "roundness": { "type": 2 },
      "seed": 1733100000001,
      "version": 1,
      "versionNonce": 1733100000001,
      "isDeleted": false,
      "boundElements": [
        { "id": "text-api-1", "type": "text" },
        { "id": "arrow-api-func", "type": "arrow" }
      ],
      "updated": 1733100000000,
      "link": null,
      "locked": false
    },
    {
      "type": "text",
      "id": "text-api-1",
      "x": 120,
      "y": 120,
      "width": 100,
      "height": 30,
      "strokeColor": "#1e1e1e",
      "backgroundColor": "transparent",
      "fillStyle": "solid",
      "strokeWidth": 2,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "angle": 0,
      "groupIds": [],
      "frameId": null,
      "index": "a1",
      "roundness": null,
      "seed": 1733100000002,
      "version": 1,
      "versionNonce": 1733100000002,
      "isDeleted": false,
      "boundElements": null,
      "updated": 1733100000000,
      "link": null,
      "locked": false,
      "text": "API",
      "fontSize": 16,
      "fontFamily": 1,
      "textAlign": "center",
      "verticalAlign": "middle",
      "containerId": "ellipse-api-1",
      "originalText": "API",
      "autoResize": true,
      "lineHeight": 1.25
    },
    {
      "type": "rectangle",
      "id": "rect-func-1",
      "x": 340,
      "y": 100,
      "width": 180,
      "height": 70,
      "strokeColor": "#7048e8",
      "backgroundColor": "#d0bfff",
      "fillStyle": "solid",
      "strokeWidth": 2,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "angle": 0,
      "groupIds": [],
      "frameId": null,
      "index": "a2",
      "roundness": { "type": 3 },
      "seed": 1733100000003,
      "version": 1,
      "versionNonce": 1733100000003,
      "isDeleted": false,
      "boundElements": [
        { "id": "text-func-1", "type": "text" },
        { "id": "arrow-api-func", "type": "arrow" },
        { "id": "arrow-func-comp", "type": "arrow" }
      ],
      "updated": 1733100000000,
      "link": null,
      "locked": false
    },
    {
      "type": "text",
      "id": "text-func-1",
      "x": 360,
      "y": 120,
      "width": 140,
      "height": 30,
      "strokeColor": "#1e1e1e",
      "backgroundColor": "transparent",
      "fillStyle": "solid",
      "strokeWidth": 2,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "angle": 0,
      "groupIds": [],
      "frameId": null,
      "index": "a3",
      "roundness": null,
      "seed": 1733100000004,
      "version": 1,
      "versionNonce": 1733100000004,
      "isDeleted": false,
      "boundElements": null,
      "updated": 1733100000000,
      "link": null,
      "locked": false,
      "text": "getData()",
      "fontSize": 16,
      "fontFamily": 1,
      "textAlign": "center",
      "verticalAlign": "middle",
      "containerId": "rect-func-1",
      "originalText": "getData()",
      "autoResize": true,
      "lineHeight": 1.25
    },
    {
      "type": "rectangle",
      "id": "rect-comp-1",
      "x": 620,
      "y": 100,
      "width": 180,
      "height": 70,
      "strokeColor": "#2f9e44",
      "backgroundColor": "#b2f2bb",
      "fillStyle": "solid",
      "strokeWidth": 2,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "angle": 0,
      "groupIds": [],
      "frameId": null,
      "index": "a4",
      "roundness": { "type": 3 },
      "seed": 1733100000005,
      "version": 1,
      "versionNonce": 1733100000005,
      "isDeleted": false,
      "boundElements": [
        { "id": "text-comp-1", "type": "text" },
        { "id": "arrow-func-comp", "type": "arrow" }
      ],
      "updated": 1733100000000,
      "link": null,
      "locked": false
    },
    {
      "type": "text",
      "id": "text-comp-1",
      "x": 640,
      "y": 120,
      "width": 140,
      "height": 30,
      "strokeColor": "#1e1e1e",
      "backgroundColor": "transparent",
      "fillStyle": "solid",
      "strokeWidth": 2,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "angle": 0,
      "groupIds": [],
      "frameId": null,
      "index": "a5",
      "roundness": null,
      "seed": 1733100000006,
      "version": 1,
      "versionNonce": 1733100000006,
      "isDeleted": false,
      "boundElements": null,
      "updated": 1733100000000,
      "link": null,
      "locked": false,
      "text": "Component.vue",
      "fontSize": 16,
      "fontFamily": 1,
      "textAlign": "center",
      "verticalAlign": "middle",
      "containerId": "rect-comp-1",
      "originalText": "Component.vue",
      "autoResize": true,
      "lineHeight": 1.25
    },
    {
      "type": "arrow",
      "id": "arrow-api-func",
      "x": 240,
      "y": 135,
      "width": 100,
      "height": 0,
      "strokeColor": "#1e1e1e",
      "backgroundColor": "transparent",
      "fillStyle": "solid",
      "strokeWidth": 2,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "angle": 0,
      "groupIds": [],
      "frameId": null,
      "index": "a6",
      "roundness": { "type": 2 },
      "seed": 1733100000007,
      "version": 1,
      "versionNonce": 1733100000007,
      "isDeleted": false,
      "boundElements": null,
      "updated": 1733100000000,
      "link": null,
      "locked": false,
      "points": [[0, 0], [100, 0]],
      "lastCommittedPoint": null,
      "startBinding": { "elementId": "ellipse-api-1", "focus": 0, "gap": 1, "fixedPoint": null },
      "endBinding": { "elementId": "rect-func-1", "focus": 0, "gap": 1, "fixedPoint": null },
      "startArrowhead": null,
      "endArrowhead": "arrow",
      "elbowed": false
    },
    {
      "type": "arrow",
      "id": "arrow-func-comp",
      "x": 520,
      "y": 135,
      "width": 100,
      "height": 0,
      "strokeColor": "#1e1e1e",
      "backgroundColor": "transparent",
      "fillStyle": "solid",
      "strokeWidth": 2,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "angle": 0,
      "groupIds": [],
      "frameId": null,
      "index": "a7",
      "roundness": { "type": 2 },
      "seed": 1733100000008,
      "version": 1,
      "versionNonce": 1733100000008,
      "isDeleted": false,
      "boundElements": null,
      "updated": 1733100000000,
      "link": null,
      "locked": false,
      "points": [[0, 0], [100, 0]],
      "lastCommittedPoint": null,
      "startBinding": { "elementId": "rect-func-1", "focus": 0, "gap": 1, "fixedPoint": null },
      "endBinding": { "elementId": "rect-comp-1", "focus": 0, "gap": 1, "fixedPoint": null },
      "startArrowhead": null,
      "endArrowhead": "arrow",
      "elbowed": false
    }
  ],
  "appState": {
    "gridSize": 20,
    "gridStep": 5,
    "gridModeEnabled": false,
    "viewBackgroundColor": "#ffffff"
  },
  "files": {}
}
```

## Best Practices

### 1. Always Validate JSON
Ensure the output is valid JSON before writing to file.

### 2. Use Descriptive IDs
IDs should indicate the element's purpose for easier debugging.

### 3. Consistent Styling
Follow the color palette for semantic meaning across diagrams.

### 4. Proper Binding
When connecting elements, always update `boundElements` on both shapes AND set bindings on arrows.

### 5. Reasonable Spacing
Maintain consistent gaps between elements for readability.

### 6. Bilingual Labels
For international teams, use format: `中文名\nEnglish Name`

## File Naming Convention

Name files descriptively:
- `{feature}-dataflow.excalidraw` - Data flow diagrams
- `{component}-architecture.excalidraw` - Architecture diagrams
- `{process}-flowchart.excalidraw` - Flowcharts

## Opening Generated Files

Generated `.excalidraw` files can be opened with:
1. **VS Code** - Install [Excalidraw extension](https://marketplace.visualstudio.com/items?itemName=pomdtr.excalidraw-editor)
2. **Web** - Upload to [excalidraw.com](https://excalidraw.com)
3. **Obsidian** - With Excalidraw plugin
