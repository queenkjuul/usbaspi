# USB drivers for MS-DOS

## Companion to "Installing Windows 98 from USB" on youtube

### Method 1

Use Method 1 if you:

- need to partition/format the target HDD before installation
- you are writing your boot floppy on a modern machine (WinXP/Win7+/Linux/MacOS)

1. Write `win95installBoot.img` to a floppy disk using whatever method is appropriate
2. Boot the floppy on your target system
3. Partition and format the HDD as necessary using `fdisk` and `format`
4. Run `edit A:\config.sys`
5. In the `[menu]` section of `CONFIG.SYS`, add a new menu entry that reads:

    ```menuitem=USBASPI, Load USB Drivers (USBASPI)```
6. Below, add a new config entry (anywhere below the `[menu]` section and above the `[config]` section) which reads:

    ```
    [USBASPI]
    device=USBASPI.SYS /V
    device=USBCD.SYS /D:MSCD001
    device=DI1000DD.SYS
    ```
    note: DI1000DD.SYS is only necessary for USB flash drive support

7. Reboot the machine and select the `USBASPI` menu item at boot
8. You should see boot messages showing your USB CDROM is detected and assigned a drive letter (we are going to use `E:\` but replace with whatever drive letter is assigned to your drive)
9. Assuming your Windows 98 CDROM is inserted, run the following commands (text below shows the drive letter prompt which should be present - `A:>` is the initial prompt after boot):

    ```
    A:>E:
    E:>copy . C:
    E:>C:
    C:>setup.exe
    ```
10. Install Windows, enjoy 😊

### Method 2

Use Method 2 if you:

- Can only create a bootable floppy using another DOS machine
- You do not need to format or partition your target HDD

1. Create a DOS boot floppy (from a running DOS machine, run `format A: /s`, or whatever method you prefer)
2. Copy all of these files to the floppy, overwriting anything present:

    ```
    AUTOEXEC.BAT
    CONFIG.SYS
    DI1000DD.SYS
    MSCDEX.EXE
    USBASPI.SYS
    USBCD.SYS
    ```
    note DI1000DD.SYS is only necessary for USB flash drive support
3. Boot from your new floppy
4. Switch to the drive letter assigned to your USB CDROM (we are assuming `E:` here)

    ```
    A:>E:
    E:>
    ```
5. Copy and run the setup files, install Windows, enjoy 😊

    ```
    E:>copy . C:
    E:>C:
    C:>setup.exe
    ```

live long and prosper, loves