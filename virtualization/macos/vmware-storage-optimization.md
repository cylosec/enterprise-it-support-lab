# macOS VMware Storage Optimization & Infrastructure Reorganization

> This documentation was created as part of ongoing infrastructure optimization and operational maintenance within my VMware/Wazuh SOC lab environment running on macOS Ventura.

---

# Overview

Recently I noticed my internal Ventura SSD was getting dangerously low on storage space while running:
- VMware Fusion
- Kali Linux
- Windows Server 2019
- Wazuh/SOC tooling
- Wireshark packet captures

Initially I suspected VMware snapshots or virtual disks were consuming most of the storage, but after running a few storage analysis commands I realized the larger issue was:
- cache accumulation
- archived Wireshark PCAPs
- locally stored VMs
- general lab infrastructure growth over time

The goal was to:
- reclaim internal SSD space
- optimize virtualization storage
- improve long-term stability
- separate workloads across dedicated external drives
- organize the lab more like a real infrastructure environment

---

# Initial Storage State

## Ventura Internal SSD
Before cleanup:
- ~414 GB used out of 500 GB
- System Data exceeding 100 GB
- VMware VMs stored locally
- large packet capture archives
- excessive cache accumulation

After cleanup:
- ~263 GB used
- ~236 GB available

Approximate reclaimed storage:
- ~150 GB

---

# Analyze Top-Level Home Directory Usage

```bash
du -hd 1 ~ 2>/dev/null | sort -hr
```

## Command Breakdown
- `du` → disk usage
- `-h` → human readable sizes
- `-d 1` → show one directory level deep
- `~` → current user home directory
- `2>/dev/null` → suppress permission errors
- `sort -hr` → sort largest to smallest

## Why I Ran This
At first I thought VMware itself was consuming most of the storage, but this command quickly showed me the larger issues were hiding inside:
- Documents
- Library
- Virtual Machines.localized

This gave me a high-level view of where to investigate next.

---

# Analyze macOS Library Usage

```bash
du -hd 1 ~/Library 2>/dev/null | sort -hr | head -30
```

## Command Breakdown
- `du` → disk usage
- `-h` → human readable sizes
- `-d 1` → show one directory level deep
- `~/Library` → current user's Library directory
- `2>/dev/null` → suppress permission errors
- `sort -hr` → sort largest to smallest
- `head -30` → display top 30 results

## Why I Ran This
macOS hides a huge amount of storage usage inside the Library folder.

This helped identify:
- cache bloat
- Application Support growth
- log accumulation
- hidden macOS storage consumption

The largest offenders ended up being:
- Application Support
- Caches
- Logs

---

# Analyze Documents Folder

```bash
du -hd 1 ~/Documents | sort -hr | head -30
```

## Command Breakdown
- `du` → disk usage
- `-h` → human readable sizes
- `-d 1` → show one directory level deep
- `~/Documents` → Documents directory
- `sort -hr` → sort largest to smallest
- `head -30` → display top 30 results

## Why I Ran This
I wanted to locate large archived project folders, packet captures, ISO collections, and backups.

This immediately revealed:
- `Wireshark_logs`
- `downloads_backup_10082023`

were consuming significant space.

The Wireshark packet capture archive alone was over 30 GB.

---

# Find Large Files

```bash
find ~ -type f -size +1G 2>/dev/null
```

## Command Breakdown
- `find` → search filesystem
- `~` → current user home directory
- `-type f` → files only
- `-size +1G` → files larger than 1 GB
- `2>/dev/null` → suppress permission errors

## Why I Ran This
I wanted to identify:
- ISO files
- VM disks
- PCAP archives
- large downloads
- forgotten backups

This is one of the most useful commands for quickly identifying storage issues on Linux/macOS systems.

---

# VMware Infrastructure Migration

Originally my VMware virtual machines were stored locally on the Ventura SSD:

```text
~/Virtual Machines.localized
```

This contained:
- Kali Linux VM
- Windows Server 2019 VM
- Kali installer ISO

As the lab continued growing, keeping VMs on the internal SSD no longer made sense operationally.

---

# External Storage Architecture

## External APFS SSD (`SG-Projects`)
Purpose:
- VMware Fusion VMs
- Wazuh
- SOC lab infrastructure
- Git repositories
- security tooling
- packet captures

Filesystem:
```text
APFS (Case-sensitive)
```

I selected APFS instead of ExFAT because:
- VMware performs better on APFS
- improved snapshot handling
- better filesystem integrity
- optimized for macOS virtualization workflows

---

## External ExFAT Drive (`WD-Data-1TB`)
Purpose:
- ISO archive
- cross-platform transfers
- Windows compatibility
- backups
- portable storage

I kept this drive in ExFAT specifically because Windows systems can read/write it natively.

---

# Create External VMware Directory

```bash
mkdir -p /Volumes/SG-Projects/VMs
```

## Command Breakdown
- `mkdir` → create directory
- `-p` → create parent directories if missing
- `/Volumes/SG-Projects/VMs` → target directory path

## Why I Ran This
Created a dedicated VMware datastore directory on the external APFS SSD.

---

# Move VMware Virtual Machines

```bash
mv ~/Virtual\ Machines.localized/*.vmwarevm /Volumes/SG-Projects/VMs/
```

## Command Breakdown
- `mv` → move files/directories
- `~/Virtual\ Machines.localized/` → source directory
- `*.vmwarevm` → all VMware VM packages
- `/Volumes/SG-Projects/VMs/` → destination directory

## Why I Ran This
The internal SSD was no longer the ideal place for:
- virtualization workloads
- snapshots
- lab infrastructure growth

Moving the VMs externally significantly reduced pressure on the internal Ventura SSD.

---

# Verify VMware Migration

## Verify Local VM Storage

```bash
du -sh ~/Virtual\ Machines.localized
```

## Command Breakdown
- `du` → disk usage
- `-s` → summarize total only
- `-h` → human readable sizes
- `~/Virtual\ Machines.localized` → VMware directory

## Why I Ran This
I wanted to confirm the VM migration actually completed successfully and that the local SSD was no longer storing large virtual disks.

---

## Verify External VMware Storage

```bash
du -sh /Volumes/SG-Projects/VMs/*
```

## Command Breakdown
- `du` → disk usage
- `-s` → summarize totals
- `-h` → human readable sizes
- `/Volumes/SG-Projects/VMs/*` → all VMs in external datastore

## Why I Ran This
Confirmed:
- both VMs successfully transferred
- VM sizes matched expected values
- datastore structure was correct

---

# VMware Performance Optimization

After migration I noticed VM startup performance became slower temporarily, although runtime performance remained normal afterward.

I suspected:
- Spotlight indexing
- Time Machine scanning
- VMware metadata rebuilding

were causing additional overhead.

---

# Exclude VMware Drive from Spotlight

Path:
```text
System Settings → Siri & Spotlight → Spotlight Privacy
```

Add:
```text
/Volumes/SG-Projects
```

## Why I Did This
Spotlight aggressively indexes:
- `.vmwarevm`
- `.vmdk`
- snapshots
- VMware metadata

This can significantly impact VM startup performance.

---

# Exclude VMware Storage from Time Machine

Path:
```text
System Settings → General → Time Machine → Options
```

Add:
```text
/Volumes/SG-Projects
```

## Why I Did This
VM files change constantly.

Allowing Time Machine to continuously scan VM disks can create unnecessary performance overhead and excessive snapshot activity.

---

# Cache Cleanup

```bash
rm -rf ~/Library/Caches/*
```

## Command Breakdown
- `rm` → remove files/directories
- `-r` → recursive deletion
- `-f` → force deletion
- `~/Library/Caches/*` → all user cache contents

## Why I Ran This
Cache accumulation inside the macOS Library folder was consuming a surprisingly large amount of storage.

This cleanup significantly reduced:
- System Data
- hidden cache accumulation
- temporary application data

---

# Log Cleanup

```bash
rm -rf ~/Library/Logs/*
```

## Command Breakdown
- `rm` → remove files/directories
- `-r` → recursive deletion
- `-f` → force deletion
- `~/Library/Logs/*` → all user logs

## Why I Ran This
The Logs directory had accumulated:
- application logs
- crash reports
- diagnostic logs

which were no longer operationally necessary.

---

# Wireshark Packet Capture Cleanup

After reviewing the Documents directory, I discovered an old packet capture archive consuming over 30 GB.

Most of these captures had already been backed up externally.

---

## Remove Archived Packet Captures

```bash
rm -rf ~/Documents/Wireshark_logs
```

## Command Breakdown
- `rm` → remove files/directories
- `-r` → recursive deletion
- `-f` → force deletion
- `~/Documents/Wireshark_logs` → packet capture archive

## Why I Ran This
The archived packet captures were no longer necessary on the internal SSD and had become one of the largest storage consumers in the environment.

---

# Verify USB Throughput

```bash
system_profiler SPUSBDataType | grep -E "Speed|Vendor ID|Product ID"
```

## Command Breakdown
- `system_profiler` → macOS hardware/system reporting utility
- `SPUSBDataType` → USB subsystem information
- `grep` → filter matching text
- `-E` → extended regex matching
- `"Speed|Vendor ID|Product ID"` → search patterns

## Why I Ran This
After moving VMs externally I wanted to verify the SSD was not accidentally negotiating at USB 2.0 speeds.

Result:
```text
Speed: Up to 5 Gb/s
```

This confirmed the SSD connection itself was healthy.

---

# Final Thoughts

This cleanup turned into much more than simply deleting files.

It became an exercise in:
- infrastructure organization
- virtualization optimization
- storage lifecycle management
- operational troubleshooting
- workload separation

The final architecture now separates:
- operating system workloads
- virtualization infrastructure
- archival storage
- cross-platform transfer storage

which feels much closer to how I would organize systems in a production or enterprise-style environment.

---

# Operational Lessons Learned

This process reinforced several important concepts:
- packet captures grow extremely fast over time
- virtualization environments require storage planning
- cache accumulation can become significant on macOS
- external APFS storage works well for VMware Fusion
- Spotlight/Time Machine can impact virtualization performance
- operational documentation is extremely valuable for repeatability