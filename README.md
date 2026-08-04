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

If MLVFS bundle is located in other directory than:

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

# DaVinci Resolve Workflow if DNG sequences do not auto-sync WAV audio (happens with 60fps footage using 5dmk3, not sure about the other modes/cameras)

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

* This exact version of Dokan is required.
* Update batch paths if moving the installation.
* Adjust MLVFS arguments in .bat file if necessary

# Credits

Magic Lantern community & Dokan Project 
