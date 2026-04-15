# Multi-Container Runtime

## Team Information

-   Name: Adil Ahmed
-   SRN: PES2UG24AM013
-   Name: Abhyudaya M. Hegde
-   SRN: PES2UG24AM009

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

### Multi-container supervision
Shows the supervisor process running and managing multiple containers (`alpha` and `beta`) simultaneously.
<img width="1269" height="305" alt="Screenshot 2026-04-14 202919" src="https://github.com/user-attachments/assets/b80eeaec-2389-446a-aedd-6a31b310e7f8" />

### Metadata tracking (ps)
Displays the output of the `ps` command, showing container IDs, process IDs, and their current states managed by the supervisor.
<img width="583" height="109" alt="Screenshot 2026-04-14 203259" src="https://github.com/user-attachments/assets/66be92ea-048e-42ee-ae22-4feb98ad10c8" />

### Bounded-buffer logging
Shows the contents of the container log file (`alpha.log`), demonstrating that container output is captured and written through the producer-consumer logging pipeline.
<img width="489" height="115" alt="Screenshot 2026-04-14 201914" src="https://github.com/user-attachments/assets/6d220c04-fbf8-4a0d-961a-1898f34dd4e8" />

### Stop command
Shows the `stop` command being issued to terminate a running container and the supervisor confirming the action.
<img width="552" height="35" alt="Screenshot 2026-04-14 203124" src="https://github.com/user-attachments/assets/62002ff9-df79-48d4-97ca-5d39bc9968d6" />

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
