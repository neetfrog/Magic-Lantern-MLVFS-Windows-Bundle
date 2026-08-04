# Magic Lantern MLVFS Windows Bundle

A complete Windows bundle for **Magic Lantern MLVFS** that includes everything needed to mount `.MLV` files as a virtual drive on Windows.

This package includes MLVFS, Dokan, and an optional Windows Explorer right-click integration, allowing MLV folders to be mounted without using the command line.

## Features

* Mount Magic Lantern `.MLV` files as a virtual drive
* No need to manually use command line after setup
* Windows Explorer right-click mounting option
* Includes required Dokan filesystem driver
* Designed for easier workflow with DaVinci Resolve

---

# Installation

## 1. Install Dokan

Run:

```text
DokanSetup.exe
```

and complete the installation.

Restart Windows if required.

---

## 2. Extract MLVFS Bundle

Extract the repository to:

```text
C:\MLVFS
```

The included scripts assume this location.

If you install it somewhere else, you will need to update the paths in the scripts.

---

# Command Line Usage

Open **Command Prompt as Administrator**.

## Mount MLV Folder

Navigate to the MLVFS folder:

```bat
cd C:\MLVFS\MLVFS_x64_lossless
```

Run:

```bat
mlvfs_x64_lossless.exe Z:\ --mlv-dir=C:\MLVDirectory --resolve-naming
```

Change the following values:

* `Z:\`
  The drive letter where the MLV files will be mounted.

* `C:\MLVDirectory`
  The folder containing your `.MLV` files.

Example:

```bat
mlvfs_x64_lossless.exe X:\ --mlv-dir=D:\Camera\MLV --resolve-naming
```

After mounting, the virtual drive will appear in Windows Explorer.

---

# Unmounting

To unmount the virtual drive:

Open **Command Prompt as Administrator**.

Navigate to the Dokan installation directory:

```bat
cd "C:\Program Files\Dokan\Dokan Library-1.0.3"
```

Run:

```bat
dokanctl.exe /u
```

> The Dokan folder name may be different depending on the installed version.

---

# Windows Explorer Right-Click Mounting

The bundle includes a Windows Explorer context menu option for easier mounting.

## Enable Right-Click Menu

Run:

```text
RightClickMountFolder\UpdateMenu.reg
```

This adds:

```text
Mount folder with MLVFS
```

to the Windows Explorer right-click menu.

After installation:

1. Right-click a folder containing `.MLV` files.

2. Select:

   ```
   Mount folder with MLVFS
   ```

3. The folder will automatically mount as a virtual drive.

![Windows Explorer right-click menu](https://i.ibb.co/gLBJ3HDb/image.png)

---

## Custom Installation Location

The right-click scripts expect MLVFS to be located at:

```text
C:\MLVFS
```

If your installation is somewhere else, edit:

```text
RightClickMountFolder\MLV_Controller.bat
```

and update the paths accordingly.

---

# DaVinci Resolve Workflow (60fps Footage)

When importing 60fps footage into DaVinci Resolve, the audio from the `.wav` files is not automatically synchronized with the DNG image sequences.

The recommended workflow is to sync audio inside the **Media** workspace before editing.

---

## Sync Audio With DNG Clips

For each DNG sequence:

1. Open the **Media** workspace.

2. Select:

   * The `.dng` clip
   * The matching `.wav` file with the same filename

3. Right-click and select:

```text
Audio Sync > Auto Sync Audio
```

4. Choose:

```text
Sync Method: Based on Timecode
```

5. Repeat for every matching DNG + WAV pair.

Currently, there does not appear to be a reliable way to batch sync all DNG and WAV pairs automatically.

---

## Add Synced Clips to Timeline

After syncing:

1. Go to the **Edit** page.
2. Select the synced DNG clips.
3. Drag them into the timeline.

The audio will now be embedded with the DNG clips.

---

## Filtering DNG Clips in Media Pool

The MLVFS workflow may create additional files such as preview GIFs or WAV files.

To quickly select only the video clips:

1. Open the Media Pool.
2. Use the search/filter option.
3. Search for:

```text
dng
```

4. Select the DNG clips and drag them into the timeline.

---

## Why Use Audio Sync Instead of Linking Clips?

Manually linking video and audio clips in the Edit page works, but it has limitations.

Using:

```text
Audio Sync > Auto Sync Audio
```

creates a properly synchronized clip inside Resolve and provides better editing behavior.

Advantages:

* Proper audio retiming controls
* Better clip management
* More reliable timeline editing
* Audio stays attached to the source clip

For high frame rate MLV footage (such as 60fps), syncing through the Media workspace gives the best results.

---

# Notes

* Run MLVFS with Administrator privileges.
* Dokan must be installed before mounting MLV folders.
* The right-click mounting script assumes the default installation path.
* If paths are changed, update the batch scripts.
* Use `--resolve-naming` to avoid filename conflicts when multiple clips contain similarly named frames.

---

# Credits

* **Magic Lantern developers** — MLVFS and MLV tools
* **Dokan Project** — Windows filesystem driver
