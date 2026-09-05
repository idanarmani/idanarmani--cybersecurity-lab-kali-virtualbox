# Cybersecurity Lab: Kali Linux & Windows 10 on VirtualBox with Custom NAT Networking

A hands-on virtual lab environment built to practice network configuration, virtualization, and cross-VM connectivity troubleshooting using Oracle VirtualBox.

## 📋 Overview

This project documents a two-phase lab setup:

- **Phase 1** — Built a virtualized Kali Linux environment from scratch: installed VirtualBox, created a custom NAT Network on the `10.0.0.0/24` subnet, imported a Kali Linux VM, and configured its IP settings.
- **Phase 2** — Added a Windows 10 VM to the same network, and verified two-way connectivity between both machines using ping tests.

## 🛠️ Tools & Environment

| Component | Detail |
|---|---|
| Hypervisor | Oracle VirtualBox 7.2.16 |
| VM 1 | Kali Linux 2026.2 (prebuilt VirtualBox image) |
| VM 2 | Windows 10 |
| Network | Custom NAT Network (`NatNetwork1`), subnet `10.0.0.0/24` |
| Archive Tool | 7-Zip 26.02 |

## 🔧 What I Did

1. Installed 7-Zip and VirtualBox on the host machine.
2. Created a custom NAT Network in VirtualBox configured for the `10.0.0.0/24` subnet.
3. Imported a prebuilt Kali Linux VM and attached it to the custom network.
4. Installed a Windows 10 VM and joined it to the same network.
5. Verified IP configuration on both machines (`ip a` on Kali, `ipconfig` on Windows).
6. Ran two-way ping tests between both VMs to confirm connectivity.
7. Took snapshots of both VMs once the working configuration was confirmed.

## 🐛 Troubleshooting Highlights

Real issues I ran into and resolved — documented in full in the report:

- **NAT Network subnet mismatch**: the custom network defaulted to `10.0.2.0/24` instead of the required `10.0.0.0/24`. Fixed by correcting the IPv4 Prefix in VirtualBox's Network Manager and restarting both the VM and VirtualBox itself to clear cached network state.
- **Windows blocking inbound pings**: pings from Kali → Windows failed with 100% packet loss until the Windows Defender Firewall inbound ICMPv4 Echo Request rules were enabled.

## 📄 Full Report

See [`Phase1_and_Phase2_Lab_Report.pdf`](./Phase1_and_Phase2_Lab_Report.pdf) for the complete step-by-step writeup with screenshots, including the troubleshooting process for both issues above.

---
*This lab is part of ongoing internship cybersecurity and networking practice.*
