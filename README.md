# Driver Backup Manager --- By NORTH

**Driver Backup Manager --- By NORTH** is a Windows utility for
exporting installed third-party driver packages before formatting or
reinstalling Windows, then reinstalling compatible drivers offline
afterward.

``` text
Driver Backup Manager - By NORTH.exe
```

## Features

``` text
[1] Export all third-party Windows drivers
[2] Restore drivers from an offline backup
[3] Create installed-driver inventory
[4] Open Driver Backups folder
[0] Exit
```

### 1. Export all third-party Windows drivers

Use this option **before formatting or reinstalling Windows**.

The tool uses Microsoft's **DISM** driver export functionality to copy
third-party driver packages from the Windows Driver Store to the
selected USB flash drive, external SSD, or external HDD.

A backup is stored under:

``` text
Driver Backups\COMPUTER_DATE\Drivers
```

The tool also records:

-   Installed driver inventory
-   Computer manufacturer and model
-   System type
-   Windows edition
-   Windows version and build
-   OS architecture
-   Backup date and DISM result

### 2. Restore drivers from an offline backup

Use this option **after reinstalling Windows**.

Select the external drive and one of the previously created driver
backups.

The application uses Microsoft's **PnPUtil** to scan the backed-up
`.inf` packages and install compatible drivers, including packages
stored in subdirectories.

This allows supported drivers to be restored **without requiring an
Internet connection**.

> \[!NOTE\] Windows determines which driver packages are compatible with
> the current hardware. A backed-up package is not automatically forced
> onto incompatible hardware.

### 3. Create installed-driver inventory

Creates a CSV inventory of currently installed signed Plug and Play
drivers.

Information includes:

-   Device name
-   Manufacturer
-   Driver provider
-   Driver version
-   Driver date
-   INF name

This option creates an inventory only; it does not export the actual
driver packages.

### 4. Open Driver Backups folder

Opens the `Driver Backups` directory on the selected USB or external
drive in Windows File Explorer.

## Recommended Workflow

Before reinstalling Windows:

``` text
1. Connect a USB flash drive or external drive.
2. Launch Driver Backup Manager - By NORTH.exe.
3. Select option [1].
4. Select the destination drive.
5. Wait for DISM to finish exporting the drivers.
6. Verify that the Driver Backups folder contains the exported packages.
```

After reinstalling Windows:

``` text
1. Complete the initial Windows installation.
2. Connect the drive containing the driver backup.
3. Launch Driver Backup Manager - By NORTH.exe.
4. Select option [2].
5. Select the backup.
6. Type INSTALL when prompted.
7. Allow PnPUtil to install compatible drivers.
8. Restart Windows if required.
```

## External Drive Detection

The application detects removable volumes and storage devices connected
through USB.

When several compatible drives are connected, it displays information
such as:

-   Drive letter
-   Volume label
-   Free space
-   Total capacity
-   Device model

## Administrator Rights

Driver export and installation operations require administrator
privileges.

When necessary, the tool relaunches itself using Windows administrator
elevation.

## Backup Structure

Example:

``` text
Driver Backups/
└── MY-PC_2026-09-30_19-00-00/
    ├── Drivers/
    │   ├── oem0.inf_amd64_.../
    │   ├── oem1.inf_amd64_.../
    │   └── ...
    ├── Info/
    │   ├── Driver_Inventory.csv
    │   ├── Computer.json
    │   └── Windows.json
    └── Backup_Info.json
```

## Requirements

-   Windows 10 or Windows 11
-   Administrator access
-   USB flash drive, external SSD, or external HDD
-   Enough free space for the exported driver packages

## Important Limitations

The tool primarily exports **third-party driver packages stored by
Windows**.

It does not guarantee backup of every:

-   Manufacturer utility
-   GPU control application
-   Firmware updater
-   OEM application
-   Microsoft Store companion application
-   Vendor-specific installer

For critical systems, keep copies of important chipset, network,
storage, GPU, and manufacturer-provided installation packages as an
additional backup.

## Safety

Verify that the driver backup completed successfully before formatting
Windows.

For important systems, keep another independent copy of the driver
backup.

## Author

Developed by **NORTH**.

## Disclaimer

This software is provided as a driver backup and restoration utility.

Hardware compatibility and driver installation remain controlled by
Windows and the individual driver packages. The author is not
responsible for missing drivers, incompatible packages, hardware
problems, interrupted operations, or data loss.
