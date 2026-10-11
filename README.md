# Folder Guard

**Folder Guard** is a lightweight, local desktop application built with C# and Windows Forms (.NET Framework) that allows users to protect sensitive folders on Windows operating systems using secure password encryption.

By utilizing Windows Access Control Lists (ACL) and standard encryption algorithms, Folder Guard secures directories against unauthorized access, modification, or visibility without requiring background services or external dependencies.

## Features

- **Password Protection**: Secure any selected folder with a master password.
  
- **Access Control Enforcement**: Restricts access rights using native Windows Security ACLs.
  
- **Easy Lock/Unlock Workflow**: Toggle protection on and off seamlessly via an intuitive Graphical User Interface (GUI).
  
- **Folder Browsing Integration**: Integrated Windows Folder Browser dialog for quick directory selection.
  
- **Lightweight & Fast**: Minimal memory footprint with zero background resource consumption when idle.
  
- **Local Security**: Stores no data in external clouds; all security policies are managed locally on your machine.
  

## Technical Architecture & How It Works

Folder Guard operates by combining **Access Control List (ACL) manipulation** with **Data Encryption Standard (DES / AES)** techniques to restrict directory navigation:

1. **Locking Mechanism**:
  
  - The application retrieves the folder path selected by the user.
    
  - It modifies the directory permissions (`DirectorySecurity` and `FileSystemAccessRule`) for the current Windows user/group, revoking read, write, and list permissions.
    
  - Folder metadata or path tokens are hashed/encrypted using the user-provided password and saved securely.
    
2. **Unlocking Mechanism**:
  
  - The user selects a locked directory and enters their password.
    
  - The app verifies the password against the cryptographic hash.
    
  - Upon successful authentication, standard access permissions (`FileSystemRights.FullControl`) are restored to the folder ACL.
    

## Prerequisites

To compile or run Folder Guard, ensure your system meets the following requirements:

- **Operating System**: Windows 7 / 8 / 10 / 11 (Requires Administrator privileges to modify NTFS folder security permissions).
  
- **Runtime Environment**: .NET Framework 4.7.2 (or higher).
  
- **IDE (for building)**: Visual Studio 2019 / 2022 with **.NET desktop development** workload installed.
  
    
    

## Security & Disclaimer

> **Important Security Notice**:
> 
> - **Password Recovery**: Folder Guard does not maintain a cloud account system or recovery server. If you forget your password or delete application config files, folder recovery will require manual ACL ownership reassignment via advanced Windows Administrator command-line tools (`takeown` and `icacls`).
>   
> - **Intended Use**: This tool provides standard local protection against unauthorized local users on Windows. It is **not** a replacement for full-disk encryption solutions like Microsoft BitLocker or VeraCrypt.
>   
