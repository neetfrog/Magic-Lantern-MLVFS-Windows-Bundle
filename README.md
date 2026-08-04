Magic Lantern MLVFS Windows Bundle, includes all the files needed to mount MLV files on Windows and a script for right click to mount so user doesn't need to use command line.



CMD method:

1. install Dokan [DokanSetup.exe]

2. Open CMD as administrator

1) cd C:\MLVFS\MLVFS_x64_lossless <- change directory to where MLVFS is located
2) .\mlvfs_x64_lossless.exe Z:\ --mlv-dir=C:\MLVDirectory --resolve-naming <- change disk/directory to where MLV files are located

to unmount run

1) cd C:\Program Files\Dokan\Dokan Library-1.0.3\dokanctl.exe
2) dokanctl.exe /u

Right-click method:

run UpdateMenu.reg inside RightClickMountFolder and this will add Mount folder with MLVFS option to windows explorer right click menu. If you have your mlvfs folder somewhere else than C:/MLVFS you will have to edit the MLV_Controller.bat script accordingly.


------------

