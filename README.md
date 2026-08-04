# Magic Lantern MLVFS Windows Bundle

Mount `.MLV` files as a virtual drive using **MLVFS + Dokan**.

MLVFS thread:  
https://www.magiclantern.fm/forum/index.php?topic=13152.0

---

# Install

Extract to:

```text
C:\MLVFS
```

Install Dokan:

```text
DokanSetup.exe
```

> Tested with **Dokan Library 1.0.3.1000** on Windows 11. Other versions may not work.

---

# Explorer Right-Click Mount

Run:

```text
RightClickMountFolder\UpdateMenu.reg
```

Adds:

```text
Mount folder with MLVFS
```

to Explorer.

If installed somewhere else, edit:

```text
RightClickMountFolder\MLV_Controller.bat
```

---

# Manual Mount

Run CMD as Administrator:

```bat
cd C:\MLVFS\MLVFS_x64_lossless

mlvfs_x64_lossless.exe Z:\ --mlv-dir=C:\MLVDirectory --resolve-naming
```

Change:

- `Z:\` → virtual drive letter
- `C:\MLVDirectory` → folder containing `.MLV` files

Unmount:

```bat
dokanctl.exe /u
```

(location: `C:\Program Files\Dokan\Dokan Library-1.0.3`)

---

# DaVinci Resolve

For DNG + WAV clips that do not auto-sync:

1. Media workspace
2. Select `.dng` + `.wav`
3. Right-click:

```text
Audio Sync → Auto Sync Audio → Based on Timecode
```

4. Drag synced clips to timeline.

Tip:

```text
Filter Media Pool: dng
```

---

# Common MLVFS Options

## Recommended

```text
--resolve-naming
```

Resolve-compatible DNG filenames.

## Processing

```text
--cs2x2 / --cs3x3 / --cs5x5
```

Chroma smoothing.

```text
--bad-pix
--really-bad-pix
```

Bad pixel correction.

```text
--fix-pattern-noise
```

Shadow row/column noise reduction (slow).

```text
--stripes
```

Highlight stripe correction.

```text
--deflicker=N
```

Per-frame exposure compensation.

## Dual ISO

```text
--dual-iso-preview
```
Fast preview.

```text
--dual-iso
```
High-quality render.

Interpolation:

```text
--amaze-edge   (quality)
--mean23       (speed)
```

## Web GUI

```text
--port=8000
--fps=N
```

## Info

```text
--version
```

---

# Credits

Magic Lantern community  
Dokan Project
