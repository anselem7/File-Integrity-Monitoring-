# File_Integrity_Monitor
## 🎬 Introduction

This project demonstrates the implementation of a basic File Integrity Monitoring (FIM) system using PowerShell. The tool monitors files for unauthorized changes by comparing their current cryptographic hashes against a previously established baseline.

File Integrity Monitoring is an essential security control that supports the Integrity component of the CIA Triad (Confidentiality, Integrity, and Availability). By continuously monitoring critical files, organizations can quickly identify unauthorized modifications, deletions, or additions that may indicate malicious activity or system compromise.

## 📌 Objectives
- Understand the role of Integrity within the CIA Triad.
- Learn how cryptographic hashing is used to verify file integrity.
- Build a PowerShell-based File Integrity Monitoring solution.
- Detect file creation, modification, and deletion events.
- Establish a baseline of trusted files for comparison.
- Gain hands-on experience with PowerShell scripting and automation.

## 👨🏾‍💻 Technologies & Tools Used
- PowerShell
- SHA-512 Hashing Algorithm
- Get-FileHash Cmdlet
- Hash Tables (Dictionaries)
- File System Operations
- Windows Operating System

## 🔑 Key Concepts
CIA Triad
- Confidentiality: Protecting information from unauthorized access.

- Integrity: Ensuring data remains accurate, consistent, and unaltered unless modified by authorized users.

- Availability: Ensuring systems and data remain accessible when needed.

- File Integrity Monitoring (FIM): File Integrity Monitoring tracks critical files and detects unauthorized changes by comparing current file hashes against a known trusted baseline.

- Hashing: A cryptographic hash acts as a digital fingerprint for a file. Even a minor modification to a file produces a significantly different hash value, making hashing an effective method for integrity verification.

## 🗂️ Project Structure
```
Project Folder/
│
├── files/
│   ├── file1.txt
│   ├── file2.txt
│   └── ...
│
├── baseline.txt
└── fim.ps1
```
## 📂 Components
- fim.ps1:	Main monitoring script
- baseline.txt:	Stores file paths and corresponding hashes
- files/:	Directory containing monitored files

## 📄 Features
- Baseline generation using SHA-512 hashing.
- Detection of newly created files.
- Detection of modified files.
- Detection of deleted files.
- Continuous monitoring loop.
- Console-based alert notifications.
- Color-coded event messages.

## 📊 Implementation Steps

### 1. Baseline Collection

The script scans all files inside the monitored directory and:

- Calculates a SHA-512 hash for each file.
- Records file paths and hashes.
- Stores results in baseline.txt.
- Removes any existing baseline file before creating a new one.

Example format:
```
C:\files\test.txt|HASH_VALUE
```
### 2. Loading the Baseline

When monitoring begins:

- The script reads baseline.txt.
- Each line is split using the pipe (|) delimiter.
- File paths and hashes are stored in a PowerShell hash table.

Example:
```
$FileHashDictionary["C:\files\test.txt"] = "HASH_VALUE"
```
### 3. Monitoring Process

The monitoring engine runs continuously and:

- Calculates the current hash of each file.
- Compares it with the stored baseline hash.
- Reports any discrepancies.

The script pauses for one second between monitoring cycles.

## 🕵️‍♂️ Event Detection
### File Creation
Triggered when a file exists in the monitored directory but does not exist in the baseline.
```
New file detected!
```
### File Modification
Triggered when a file's current hash differs from its baseline hash.
```
File modified!
```
###File Deletion
Triggered when a file recorded in the baseline no longer exists.
```
File deleted!
```
## 📈 Core Data Structures
### Baseline File

baseline.txt

Stores:
```
<file_path>|<hash>
```
### Hash Table

Used to store baseline information in memory.

(Key) File Path	--> (Value) SHA-512 Hash

## 🧰 Functions
### CalculateFileHash()

Calculates the SHA-512 hash of a specified file.
```
Get-FileHash -Path $filePath -Algorithm SHA512
```
### EraseBaselineIfExists()

Checks for an existing baseline file and removes it before generating a new one.
```
Test-Path
Remove-Item
```

## 🧐 Skills Demonstrated
- Cybersecurity Fundamentals
- File Integrity Monitoring
- PowerShell Scripting
- Cryptographic Hashing
- Automation
- File System Monitoring
- Data Structures (Hash Tables)
- Security Operations Concepts
- Incident Detection Techniques

## ✍️ Learning Outcomes

Through this project, I gained practical experience in:

- Understanding the Integrity principle of the CIA Triad.
- Using cryptographic hashes to verify file integrity.
- Building a basic security monitoring solution in PowerShell.
- Detecting unauthorized file system changes.
- Working with PowerShell hash tables and file operations.
- Designing foundational cybersecurity automation tools.


## ✅ Conclusion

This project provides a foundational implementation of a File Integrity Monitoring system using PowerShell. By leveraging SHA-512 hashing and baseline comparisons, the solution can identify unauthorized file changes, deletions, and additions. While intentionally simple, it demonstrates core concepts used by enterprise-grade FIM solutions and serves as a strong starting point for further cybersecurity and automation projects.
