# Magic Lantern MLVFS Windows Bundle

Windows bundle for **Magic Lantern MLVFS** to mount `.MLV` files as a virtual drive. Includes MLVFS, Dokan, and an optional Explorer right-click mount option.

https://www.magiclantern.fm/forum/index.php?topic=13152.0 <- MLVFS thread on Magic Lantern forums

## Install

1. Download the repository and extract to:

```text
C:\MLVFS
```

2. Install Dokan:

```text
DokanSetup.exe
```

---

# Explorer Right-Click Mount

Run:

```text
RightClickMountFolder\UpdateMenu.reg
```

This adds **Mount folder with MLVFS** to Windows Explorer.

If MLVFS is not installed at:

```text
C:\MLVFS
```

edit:

```text
RightClickMountFolder\MLV_Controller.bat
```

![Windows Explorer right-click menu](https://i.ibb.co/gLBJ3HDb/image.png)

# Command Line Mount

Run **CMD as Administrator**:

```bat
cd C:\MLVFS\MLVFS_x64_lossless
mlvfs_x64_lossless.exe Z:\ --mlv-dir=C:\MLVDirectory --resolve-naming
```

Change:

* `Z:\` → mount drive letter
* `C:\MLVDirectory` → folder containing `.MLV` files

Unmount:

```bat
cd "C:\Program Files\Dokan\Dokan Library-1.0.3"
dokanctl.exe /u
```



---

# DaVinci Resolve (60fps Workflow)

DNG sequences do not auto-sync WAV audio.

In the **Media** workspace:

1. Select matching `.dng` + `.wav`
2. Right-click:

```text
Audio Sync > Auto Sync Audio
```

3. Select:

```text
Based on Timecode
```

Repeat for each clip pair.

Then drag the synced DNG clips from the Media Pool into the timeline.

Tip: Filter Media Pool by:

```text
dng
```

to select only DNG clips.

Using Resolve's **Audio Sync** method is preferred over manually linking audio in the timeline because it keeps proper clip/audio retiming behavior.

---

# Notes

* Run MLVFS as Administrator.
* Dokan is required.
* Update batch paths if moving the installation.
* `--resolve-naming` prevents filename conflicts.

# Credits

Magic Lantern community & Dokan Project 
