# Magic Lantern MLVFS Windows Bundle

Windows bundle for **Magic Lantern MLVFS** to mount `.MLV` files as a virtual drive.

Includes:

- MLVFS
- Dokan
- Optional Windows Explorer right-click mount integration

MLVFS forum thread:  
https://www.magiclantern.fm/forum/index.php?topic=13152.0

---

# Installation

## 1. Extract the bundle

Download and extract the repository to:

```text
C:\MLVFS
```

## 2. Install Dokan

Run:

```text
DokanSetup.exe
```

---

# Explorer Right-Click Mount

Run:

```text
RightClickMountFolder\UpdateMenu.reg
```

This adds:

```text
Mount folder with MLVFS
```

to the Windows Explorer right-click menu.

![Windows Explorer right-click menu](https://i.ibb.co/gLBJ3HDb/image.png)

## Custom installation path

If the MLVFS bundle is installed somewhere other than:

```text
C:\MLVFS
```

edit:

```text
RightClickMountFolder\MLV_Controller.bat
```

and update the paths accordingly.

---

# Command Line Mount

Open **Command Prompt as Administrator**:

```bat
cd C:\MLVFS\MLVFS_x64_lossless

mlvfs_x64_lossless.exe Z:\ --mlv-dir=C:\MLVDirectory --resolve-naming
```

Change:

| Parameter | Description |
|---|---|
| `Z:\` | Drive letter used for the virtual mount |
| `C:\MLVDirectory` | Folder containing `.MLV` files |

## Unmount

Run:

```bat
cd "C:\Program Files\Dokan\Dokan Library-1.0.3"

dokanctl.exe /u
```

---

# DaVinci Resolve Workflow

If DNG sequences do not automatically sync WAV audio:

*(Known to happen with 60fps footage from the 5D Mark III. Other cameras/modes may vary.)*

## Sync audio

In the **Media** workspace:

1. Select the matching:

```text
.dng sequence + .wav file
```

2. Right-click:

```text
Audio Sync > Auto Sync Audio
```

3. Select:

```text
Based on Timecode
```

4. Repeat for each clip pair.

Then drag the synced DNG clips from the Media Pool into the timeline.

## Tip

Filter the Media Pool using:

```text
dng
```

to show only DNG clips.

Using Resolve's built-in **Audio Sync** workflow is preferred over manually linking audio in the timeline because it preserves proper clip/audio retiming behavior.

---

# Notes

- This exact Dokan version is required:

```text
Dokan Library 1.0.3.1000
```

  Other versions did not work correctly with Windows 11 during testing.

- Adjust MLVFS options and paths in:

```text
MLV_Controller.bat
```

if required.

---

# MLVFS Options

## File / Folder Options

| Option | Description |
|---|---|
| `--mlv-dir=%s` | Directory containing MLV files |
| `--resolve-naming` | Use DNG filenames compatible with DaVinci Resolve |

---

## Processing Options

| Option | Description |
|---|---|
| `--cs2x2` | 2x2 chroma smoothing |
| `--cs3x3` | 3x3 chroma smoothing |
| `--cs5x5` | 5x5 chroma smoothing |
| `--bad-pix` | Fix bad pixels (autodetected) |
| `--really-bad-pix` | Aggressive bad pixel correction |
| `--fix-pattern-noise` | Fix row/column noise in shadows (slow) |
| `--stripes` | Vertical stripe correction in highlights (nonuniform column gains) |
| `--deflicker=%d` | Per-frame exposure compensation for flicker-free video. Raw processor must interpret the BaselineExposure DNG tag |

---

## Dual ISO Options

| Option | Description |
|---|---|
| `--dual-iso-preview` | Preview Dual ISO files (fast) |
| `--dual-iso` | Render Dual ISO files (high quality) |
| `--amaze-edge` | Dual ISO interpolation method (high quality) |
| `--mean23` | Dual ISO interpolation method (fast) |
| `--no-alias-map` | Disable alias map |
| `--alias-map` | Enable alias map |

---

## Web GUI Options

| Option | Description |
|---|---|
| `--port=%s` | Port used for Web GUI (default: `8000`) |
| `--fps=%f` | FPS used for playback in Web GUI |

---

## Diagnostic Options

| Option | Description |
|---|---|
| `--version` | Display MLVFS version |

---

# Credits

- Magic Lantern community
- Dokan Project
