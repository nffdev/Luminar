# Luminar - Technical Documentation

## Table of Contents

1. [Introduction](#introduction)
2. [System Architecture](#system-architecture)
3. [Deployment Mechanism](#deployment-mechanism)
4. [Environment Detection](#environment-detection)
5. [Privilege Escalation](#privilege-escalation)
6. [Kernel Driver Loading](#kernel-driver-loading)
7. [Native Function Hooking](#native-function-hooking)
8. [Persistence](#persistence)
9. [Client-Server Communication](#client-server-communication)
10. [Technical Appendices](#technical-appendices)

## Introduction

Luminar is an advanced remote monitoring and control solution designed to operate stealthily on Windows systems. This technical documentation details the internal mechanisms and techniques used to ensure its operation, stealth, and persistence.

## System Architecture

Luminar consists of several interconnected modules:

1. **Client Module**: Main executable deployed on the target system
2. **Kernel Module**: Kernel-mode driver for low-level operations
3. **Persistence Module**: Component that modifies the bootloader to ensure persistence
4. **C2 Server**: Command and control infrastructure for client management

![System Architecture](images/system_architecture.png)

## Deployment Mechanism

Luminar deployment follows a multi-stage process designed to maximize stealth and effectiveness:

```mermaid
graph TD
    A[Initial Execution] --> B{VM Detection}
    B -->|VM detected| C[Legitimate Behavior]
    B -->|Real System| D[Stealth Deployment]
    D --> E[Privilege Escalation]
    E --> F[Kernel Driver Loading]
    F --> G[NT Function Hooking]
    G --> H[Bootloader Modification]
    H --> I[Persistence Established]
```

## Environment Detection

During its initial execution, Luminar performs a series of checks to determine if it's running in a virtual environment (sandbox, virtual machine) or on a real physical system.

### VM Detection Techniques

```csharp
public static bool IsVirtualMachine()
{
    // Check hardware signatures
    if (CheckVMHardwareSignatures())
        return true;
        
    // Check for known VM artifacts
    if (CheckVMDrivers() || CheckVMServices())
        return true;
        
    
    // Timing analysis (VMs have different timing characteristics)
    if (PerformTimingAnalysis())
        return true;
        
    return false;
}
```

If a virtual machine is detected, Luminar adopts legitimate behavior to avoid detection, acting as a standard application without deploying its malicious components.

## Privilege Escalation

On a real system, Luminar proceeds to escalate privileges from standard user (USER) to administrator rights (ADMIN).
