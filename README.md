# Magic Lantern MLVFS Windows Bundle

Windows bundle for **Magic Lantern MLVFS** to mount `.MLV` files as a virtual drive.

Includes:

- MLVFS
- Dokan
- Optional Windows Explorer right-click mount option

MLVFS thread:
https://www.magiclantern.fm/forum/index.php?topic=13152.0

---

# Installation

1. Download the repository and extract it to:

C:\MLVFS

2. Install Dokan:

DokanSetup.exe

---

# Explorer Right-Click Mount

Run:

RightClickMountFolder\UpdateMenu.reg

This adds:

Mount folder with MLVFS

to Windows Explorer.

If the MLVFS bundle is located somewhere other than:

C:\MLVFS

edit:

RightClickMountFolder\MLV_Controller.bat

---

# Command Line Mount

Run CMD as Administrator:

cd C:\MLVFS\MLVFS_x64_lossless

mlvfs_x64_lossless.exe Z:\ --mlv-dir=C:\MLVDirectory --resolve-naming

Change:

Z:\  
Mount drive letter

C:\MLVDirectory  
Folder containing `.MLV` files

Unmount:

cd "C:\Program Files\Dokan\Dokan Library-1.0.3"

dokanctl.exe /u


---

# DaVinci Resolve Workflow

If DNG sequences do not automatically sync WAV audio (for example, some 60fps footage from 5D Mark III), do the following:

1. Open the Media workspace.

2. Select matching:

.dng sequence + .wav file

3. Right-click:

Audio Sync > Auto Sync Audio

4. Select:

Based on Timecode

Repeat for each clip pair.

Then drag the synced DNG clips from the Media Pool into the timeline.

Tip:

Filter Media Pool by:

dng

to show only DNG clips.

Using Resolve's Audio Sync feature is preferred over manually adding audio in the timeline because it keeps proper clip and retiming behavior.

---

# MLVFS Options

## File / Folder Options

--mlv-dir=<path>
    Directory containing MLV files

--resolve-naming
    DNG filenames compatible with DaVinci Resolve


## Processing Options

--cs2x2
    2x2 chroma smoothing

--cs3x3
    3x3 chroma smoothing

--cs5x5
    5x5 chroma smoothing

--bad-pix
    Fix bad pixels (autodetected)

--really-bad-pix
    Aggressive bad pixel fix

--fix-pattern-noise
    Fix row/column noise in shadows (slow)

--stripes
    Vertical stripe correction in highlights
    (nonuniform column gains)

--deflicker=<value>
    Per-frame exposure compensation for flicker-free video.
    Raw processor must interpret the BaselineExposure DNG tag.


## Dual ISO Options

--dual-iso-preview
    Preview Dual ISO files (fast)

--dual-iso
    Render Dual ISO files (high quality)

--amaze-edge
    Dual ISO interpolation method (high quality)

--mean23
    Dual ISO interpolation method (fast)

--no-alias-map
    Disable alias map

--alias-map
    Enable alias map


## Web GUI Options

--port=<value>
    Port used for web GUI (default: 8000)

--fps=<value>
    FPS used for playback in web GUI


## Diagnostic Options

--version
    Display MLVFS version


---

# Notes

- Dokan version 1.0.3.1000 is required.
- Other Dokan versions did not work with Windows 11 during testing.
- Adjust MLVFS options and paths in MLV_Controller.bat if necessary.


---

# Credits

Magic Lantern community & Dokan Project
