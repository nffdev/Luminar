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
