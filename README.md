# Magic Lantern MLVFS Windows Bundle

A Windows bundle for **Magic Lantern MLVFS** that includes everything needed to mount `.MLV` files as a virtual drive on Windows. It also provides an optional Windows Explorer right-click menu, so mounting can be done without using the command line.

## Features

* Complete Windows MLVFS bundle
* Includes Dokan installer
* Mount `.MLV` files without using the command line
* Optional Windows Explorer right-click integration

## Installation

1. Download this repository as a ZIP file.

2. Extract it to:

   ```text
   C:\MLVFS
   ```

3. Run `DokanSetup.exe` and complete the installation.

4. (Optional) Enable the Windows Explorer context menu by running:

   ```text
   RightClickMountFolder\UpdateMenu.reg
   ```

## Usage

### Right-click method

After installing the context menu:

1. Right-click a folder containing `.MLV` files.
2. Select **Mount folder with MLVFS**.
3. The folder will be mounted automatically as a virtual drive.

If your installation is not located at `C:\MLVFS`, edit `MLV_Controller.bat` and update the path to your MLVFS installation before using the context menu.

![Windows Explorer right-click menu](https://i.ibb.co/gLBJ3HDb/image.png)

### Command line

You can also run `mlvfs.exe` manually if you prefer using the command line.

## Requirements

* Windows
* Dokan (included as `DokanSetup.exe`)
* Magic Lantern MLV files

## Notes

* The context menu scripts assume the bundle is installed in `C:\MLVFS`.
* If you move the bundle to another location, update the paths in `MLV_Controller.bat` accordingly.

## Credits

* **Magic Lantern** project for MLVFS.
* **Dokan** for providing the Windows filesystem driver.
