# Context Map Diagrams

This folder contains Mermaid diagrams visualizing the bounded context relationships.

## How to View

### Option 1: GitHub (Automatic)
GitHub automatically renders Mermaid diagrams. Just click any `.mmd` file.

### Option 2: Mermaid Live Editor
1. Go to https://mermaid.live
2. Copy the contents of any `.mmd` file
3. Paste into the editor
4. Export as PNG/SVG if needed

## Available Diagrams

### Comprehensive Context Map
**File**: `context-map-comprehensive.mmd`

All bounded contexts and their relationships

### Memory Layer (System of Record)
**File**: `context-map-memory-layer.mmd`

Reference data and directory contexts

### Heart Layer (Lifecycle/Relationship)
**File**: `context-map-heart-layer.mmd`

Lifecycle and relationship management contexts

### Brain Layer (Operations/Execution)
**File**: `context-map-brain-layer.mmd`

Operational and execution contexts

### BIAN Trinity Architecture
**File**: `context-map-trinity-overview.mmd`

High-level view of Memory/Heart/Brain layers

### Integration Complexity
**File**: `context-map-complexity.mmd`

Top 5 most connected contexts


## Diagram Legend

- **💾 Blue boxes**: Memory contexts (System of Record)
- **💚 Green boxes**: Heart contexts (Lifecycle/Relationship)
- **🧠 Orange boxes**: Brain contexts (Operations/Execution)
- **⚙️ Gray boxes**: Hybrid/Technical contexts
