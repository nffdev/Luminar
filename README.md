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

## Surveillance Tools

- **KeyLogger**: Record and log keystrokes
- **Ransomware**: Encryption tool with logging capabilities

## Fun Actions

### Message Box
- Send custom message boxes to the target
- Mass open option (opens 10 simultaneously)
- Configurable message types (Error, Information, Warning)

### Chat Box
- Real-time chat interface with the target user

### Wallpaper Control
- Change the target system's desktop background

### Audio Player
- Play audio files on the target system

### Remote Interaction
- Show/Hide Taskbar
- Show/Hide Desktop
- Show/Hide Clock
- Swap/Restore Mouse Buttons
- Shake Window: Continuously move all windows
- Slider: Transform screen into puzzle that must be solved

### Browser Control
- Open specified URLs in the target's web browser

## Credential Recovery

### Applications
- **Wallets**: All cryptocurrency wallets including browser extensions
- **Discord**: Account credentials
- **FileZilla**: FTP credentials
- **FoxMail**: Email credentials
- **Ngrok**: Tunnel credentials
- **OBS**: Streaming credentials
- **Steam**: Gaming platform credentials
- **Telegram**: Messaging credentials
- **WinSCP**: Secure file transfer credentials

### Browsers
- All Chromium-based browsers
- All Gecko-based browsers

### Games
- Epic Games
- Minecraft
- Riot Games
- Uplay
- Nations Glory

### System Information
- Clipboard contents
- Screenshot capture
- System specifications (CPU, RAM, OS Version, GPU)
- Windows Product Key
- IP Address

### VPN Services
- NordVPN
- OpenVPN
- ProtonVPN

### Injections
- Discord
- Exodus
- Metamask (Coming Soon)

## User Settings

- Password management
- Client export functionality
- Account deletion options

## Technical Details

### Process Manipulation

Luminar utilizes advanced kernel-level techniques for process manipulation and monitoring:

```csharp
// Process hiding implementation using direct kernel manipulation
public static bool HideProcess(int pid)
{
    IntPtr hProcess = OpenProcess(PROCESS_ALL_ACCESS, false, pid);
    if (hProcess == IntPtr.Zero)
        return false;
        
    // Locate the EPROCESS structure in kernel memory
    IntPtr pEPROCESS = GetProcessEPROCESS(hProcess);
    
    // Unlink the process from ActiveProcessLinks
    if (UnlinkProcessFromList(pEPROCESS))
    {
        CloseHandle(hProcess);
        return true;
    }
    
    CloseHandle(hProcess);
    return false;
}
```

### Kernel-Mode Operations

The rootkit components leverage Windows kernel structures to achieve stealth:

```c
// Kernel-mode driver code for TCP connection hiding
NTSTATUS HideTcpConnection(PVOID connectionObject)
{
    PLIST_ENTRY listEntry;
    
    // Get the TCP connection list entry
    listEntry = (PLIST_ENTRY)((ULONG_PTR)connectionObject + TCP_CONN_LIST_OFFSET);
    
    // Remove from the doubly-linked list
    if (listEntry->Flink != NULL && listEntry->Blink != NULL)
    {
        listEntry->Flink->Blink = listEntry->Blink;
        listEntry->Blink->Flink = listEntry->Flink;
        
        // Clear the pointers
        listEntry->Flink = listEntry->Blink = listEntry;
        return STATUS_SUCCESS;
    }
    
    return STATUS_UNSUCCESSFUL;
}
```

### Anti-Detection Mechanisms

Luminar implements multiple layers of anti-detection:

| Technique | Implementation | Target Systems |
|-----------|----------------|----------------|
| Anti-VM | Memory timing checks, hardware ID verification | VMware, VirtualBox, QEMU |
| Anti-Debug | IsDebuggerPresent, CheckRemoteDebuggerPresent, timing checks | User-mode debuggers |
| Anti-Analysis | Code obfuscation, encrypted strings, delayed execution | Static analysis tools |

### HVNC Implementation

The Hidden VNC technology creates an invisible desktop session:

```csharp
protected override bool CreateHiddenDesktop()
{
    // Create a hidden desktop that's not visible to the user
    _hiddenDesktop = CreateDesktop("HiddenDesktop", IntPtr.Zero, IntPtr.Zero, 0, DESKTOP_CREATEWINDOW | DESKTOP_WRITEOBJECTS | DESKTOP_SWITCHDESKTOP, IntPtr.Zero);
    
    if (_hiddenDesktop == IntPtr.Zero)
        return false;
        
    // Switch to hidden desktop for operations
    if (!SwitchDesktop(_hiddenDesktop))
        return false;
        
    // Initialize hidden desktop environment
    return InitializeHiddenEnvironment();
}
```

### Encrypted Communication

All client-server communication is encrypted using a hybrid approach:

- RSA-2048 for key exchange
- AES-256 for session encryption
- HMAC-SHA256 for message authentication

The protocol implements perfect forward secrecy by generating new session keys for each connection.

## Technical Documentation

Please read the [technical documentation](Technical%20Documentation.md) to get a comprehensive and full overview of Luminar and its internals, and how to deploy and integrate it.

The technical documentation includes detailed information about:
- System architecture and deployment mechanism
- Environment detection techniques
- Privilege escalation methods
- Kernel driver loading process
- Native function hooking implementation
- Persistence mechanisms
- Client-server communication protocols
- Important data structures and kernel offsets