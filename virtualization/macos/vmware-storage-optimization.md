# macOS VMware Storage Optimization & Infrastructure Reorganization

## Overview

This document outlines the process used to optimize storage utilization on a macOS Ventura 
workstation used for:
- VMware Fusion virtualization
- Wazuh/SOC lab operations
- Windows Server administration
- Kali Linux testing
- packet capture analysis

The objective was to:
- reclaim internal SSD space
- improve virtualization stability
- separate workloads across dedicated storage devices
- optimize VMware Fusion performance
- organize long-term lab infrastructure storage

---

# Initial Storage State

## Ventura Internal SSD
Before cleanup:
- ~414 GB used out of 500 GB
- high System Data utilization
- VMware virtual machines stored locally
- large Wireshark packet capture archive
- excessive cache accumulation

After cleanup:
- ~263 GB used
- ~236 GB available

Approximate reclaimed storage:
- ~150 GB

---

# Storage Analysis Commands

## Analyze Top-Level Home Directory Usage

```bash
du -hd 1 ~ 2>/dev/null | sort -hr
```

### Explanation
- `du` → disk usage
- `-h` → human readable sizes
- `-d 1` → show one directory level deep
- `2>/dev/null` → suppress permission errors
- `sort -hr` → sort largest to smallest

Purpose:
Identify major storage consumers in the user profile.

---

## Analyze macOS Library Usage

```bash
du -hd 1 ~/Library 2>/dev/null | sort -hr | head -30
```

Purpose:
Identify:
- cache bloat
- Application Support usage
- Containers
- Logs
- hidden storage consumption

---

## Analyze Documents Folder

```bash
du -hd 1 ~/Documents | sort -hr | head -30
```

Purpose:
Locate:
- PCAP archives
- backups
- project folders
- ISO storage
- exported reports

---

## Find Large Files

```bash
find ~ -type f -size +1G 2>/dev/null
```

### Explanation
- `find ~` → search from home directory
- `-type f` → files only
- `-size +1G` → larger than 1 GB
- `2>/dev/null` → suppress permission errors

Purpose:
Locate:
- ISO images
- VM disks
- large archives
- packet captures
- forgotten downloads

---

# VMware Infrastructure Migration

## Original VM Storage Location

```text
~/Virtual Machines.localized
```

Contained:
- Kali Linux VM
- Windows Server 2019 VM
- Kali installer ISO

---

# External VMware Datastore

## Selected External SSD

Volume:
```text
SG-Projects
```

Filesystem:
```text
APFS (Case-sensitive)
```

Advantages:
- optimized for macOS
- improved VMware compatibility
- snapshot-friendly
- improved integrity vs ExFAT

---

# Create External VM Directory

```bash
mkdir -p /Volumes/SG-Projects/VMs
```

### Explanation
- `mkdir` → create directory
- `-p` → create parent directories if missing

---

# Move VMware Virtual Machines

```bash
mv ~/Virtual\ Machines.localized/*.vmwarevm /Volumes/SG-Projects/VMs/
```

Purpose:
Offload VM infrastructure from the internal SSD.

---

# Verify VM Migration

## Verify Local VM Storage

```bash
du -sh ~/Virtual\ Machines.localized
```

Purpose:
Confirm local VM storage was removed.

---

## Verify External VM Storage

```bash
du -sh /Volumes/SG-Projects/VMs/*
```

Purpose:
Confirm VMs exist on the external SSD.

---

# VMware Performance Optimization

## Exclude VMware Drive from Spotlight

Path:
```text
System Settings → Siri & Spotlight → Spotlight Privacy
```

Add:
```text
/Volumes/SG-Projects
```

Purpose:
Prevent Spotlight indexing of:
- `.vmwarevm`
- `.vmdk`
- snapshots
- VMware metadata

Improves:
- VM startup performance
- disk responsiveness

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

Purpose:
Prevent VM snapshot scanning overhead.

---

# Cache Cleanup

## Clear User Cache

```bash
rm -rf ~/Library/Caches/*
```

Purpose:
Remove:
- browser cache
- application cache
- temporary macOS data

---

# Log Cleanup

## Remove User Logs

```bash
rm -rf ~/Library/Logs/*
```

Purpose:
Remove:
- application logs
- stale crash data
- diagnostic logs

---

# Wireshark Packet Capture Cleanup

## Identify Large Packet Capture Archive

```bash
du -hd 1 ~/Documents | sort -hr
```

Result:
- `~/Documents/Wireshark_logs`
- ~32 GB

---

## Remove Archived Packet Captures

```bash
rm -rf ~/Documents/Wireshark_logs
```

Purpose:
Remove archived:
- `.pcap`
- `.pcapng`
- exported capture data

---

# USB Throughput Verification

## Verify External SSD Link Speed

```bash
system_profiler SPUSBDataType | grep -E "Speed|Vendor ID|Product ID"
```

Result:
```text
Speed: Up to 5 Gb/s
```

Purpose:
Confirm:
- USB 3.x operation
- SSD not falling back to USB 2.0

---

# Final Storage Architecture

## Internal Ventura SSD
Purpose:
- macOS
- applications
- active projects
- swap/cache
- development environment

---

## External APFS SSD (`SG-Projects`)
Purpose:
- VMware Fusion VMs
- Wazuh
- SOC lab infrastructure
- packet captures
- Git repositories
- security tooling

---

## External ExFAT Drive (`WD-Data-1TB`)
Purpose:
- cross-platform transfers
- ISO archive
- backups
- Windows compatibility

---

# Operational Lessons Learned

This process demonstrates:
- storage lifecycle management
- virtualization infrastructure optimization
- workstation resource management
- log retention considerations
- archive strategy implementation
- enterprise-style workload separation
