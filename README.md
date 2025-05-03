# Luminar - Advanced Monitoring Solution

## Overview
Luminar is a sophisticated remote monitoring solution designed for system administrators and security professionals. This tool provides comprehensive remote system management capabilities with an intuitive dashboard interface.

**Note**: This is a private project and not intended for open-source distribution.

## Dashboard Features

### Authentication & Management
- **Login & Registration System**: Secure authentication system for authorized access
- **License Management**: Subscription-based licensing system for feature access
- **Announcement System**: Platform-wide notifications for users
- **Status Monitoring**: Real-time status indicators for website, API, and builder services

### Client Management
The dashboard provides a comprehensive view of connected clients with the following information:
- PC Name
- IP Address
- Country
- GPU Information
- Operating System
- Status (Dead/Alive)
- Administrator Status
- Action Controls

![Client Management Dashboard](images/client_dashboard.png)

## Builder System

### Assembly Configuration
- **Name**: Set the application name
- **Description**: Add application description
- **Copyright**: Include copyright information
- **Product Name**: Configure product name
- **Version**: Set application version
- **File Icon**: Customize application icon

### Additional Options
- **Binder**: Combine multiple files into one executable
- **Binder Path**: Specify path for binding
- **Run as Admin**: Execute with administrative privileges
- **Run at Startup**: Launch application on system boot
- **Anti-VM**: Detection and prevention of virtual machine environments
- **Anti-Debug**: Protection against debugging attempts
- **Fake Error**: Generate deceptive error messages
- **UAC Bypass**: Technique to circumvent User Account Control in Windows, allowing applications to gain elevated privileges without prompting the user for confirmation. This method is used to execute code with administrative rights while evading security measures.

### Rootkits / Bootkits
- **(km) Hide Process**: Kernel-mode process concealment
- **(km) Hide File Folder**: Kernel-mode file/folder concealment
- **(km) Hide TCP Connection**: Kernel-mode network connection concealment
- **(km) Hide Services**: Kernel-mode service concealment
- **(km) Registry**: Kernel-mode registry manipulation
- **(km) Hide from Startup**: Kernel-mode startup concealment
- **(um) Unkillable**: User-mode process protection making termination difficult
- **(um) Watchdog**: User-mode process monitoring and auto-restart

### Tasks
The builder allows configuration of automated tasks that execute based on specific conditions when the client is launched. These tasks can be scheduled to run at specific times, on specific events, or based on system conditions.

### Clipper
The clipper functionality monitors the clipboard for cryptocurrency wallet addresses. When a user copies a cryptocurrency address, the clipper replaces it with an alternative address specified by the administrator, redirecting transactions to the specified wallet.

## Cryptocurrency Tools

### Miner Management
Displays a table with:
- IP Address
- Hardware Information
- Mining Status
- Connection Status

### Clipper Management
Similar interface to the miner management, showing:
- IP Address
- Target Cryptocurrencies
- Active Status
- Connection Status

## Remote Viewing

### Screen Viewer
- Real-time remote screen viewing

### Camera Access
- Remote camera access and viewing

### HVNC (Hidden Virtual Network Computing)
HVNC is an advanced remote control technology that creates a hidden desktop session on the target machine. Unlike traditional remote desktop solutions, HVNC operates invisibly to the user, allowing for covert remote control. This technology enables administrators to interact with the system without alerting the user to the remote session, making it useful for security monitoring and administrative tasks.

## File Explorer

The file explorer module provides comprehensive file system management:
- Browse files and directories
- Upload files to the target system
- Delete files from the target system
- Execute files on the target system
- Compress folders into zip archives

## System Manager

The system manager provides control over the target system:
- Task Manager: View and manage running processes
- System Control:
  - Blue Screen trigger
  - System restart
  - System shutdown
  - Display power control
  - Input control lock (keyboard & mouse)

## Remote Shells

Provides terminal access to the target system with full command execution capabilities.
