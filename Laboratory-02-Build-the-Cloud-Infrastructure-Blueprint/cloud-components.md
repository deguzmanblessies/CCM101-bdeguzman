# Cloud Infrastructure Components

## Compute Resources
**Purpose:** Provides the processing power (CPU/RAM) needed to run applications and workloads.
**Importance in cloud computing:** Compute is the foundation of cloud services — it executes code, whether on VMs, containers, or serverless functions.
**Relation to KillerCoda:** The KillerCoda VM itself is a compute resource — its CPU and RAM (seen via `lscpu` and `free -h`) represent the processing capacity assigned to this session.

## Storage Resources
**Purpose:** Persistently stores data, files, and system information.
**Importance in cloud computing:** Cloud storage allows data to survive beyond a single session and be accessed reliably, scaled, and backed up.
**Relation to KillerCoda:** The disk shown by `df -h` and mounted filesystems represent the storage layer available to the compute instance.

## Networking Resources
**Purpose:** Connects compute and storage resources to each other and to the internet.
**Importance in cloud computing:** Networking enables communication between services, remote access, and public availability of applications.
**Relation to KillerCoda:** The hostname and IP address (from `hostname` and `ip a`) show how this instance is identified and reached on a network.

## Operating System
**Purpose:** Manages hardware resources and provides the environment in which applications run.
**Importance in cloud computing:** The OS is the interface between cloud infrastructure and the software/services deployed on it.
**Relation to KillerCoda:** The Linux distribution identified via `cat /etc/os-release` is the OS layer running on the provisioned compute instance.
