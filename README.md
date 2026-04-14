# Multi-Container Runtime

## Team Information

-   Name: Adil Ahmed
-   SRN: `<your-srn-here>`{=html}

------------------------------------------------------------------------

## Build, Load, and Run Instructions

### Build

    make

### Load Kernel Module

    sudo insmod monitor.ko

### Start Supervisor

    sudo ./engine supervisor ./rootfs-base

### Start Containers

    sudo ./engine start alpha ./rootfs-alpha /memory_hog
    sudo ./engine start beta ./rootfs-beta /memory_hog

### List Containers

    sudo ./engine ps

### Stop Containers

    sudo ./engine stop alpha
    sudo ./engine stop beta

------------------------------------------------------------------------

## Screenshots

Place screenshots inside a folder named `screenshots/`:

-   multiple.png
-   ps.png
-   logs.png
-   start.png
-   stop.png

------------------------------------------------------------------------

## Architecture

-   Supervisor manages containers
-   Containers use namespaces and chroot
-   IPC via UNIX sockets
-   Logging via producer-consumer buffer

------------------------------------------------------------------------

## Challenges Faced

-   VirtualBox shared folder issues (no symlinks)
-   Alpine vs glibc mismatch
-   Debugging container execution