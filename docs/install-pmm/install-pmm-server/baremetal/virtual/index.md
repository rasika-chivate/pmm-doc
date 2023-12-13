# Install PMM server on the virtual machine

How to run PMM Server as a virtual machine.

!!! summary alert alert-info "Summary"
    - Download and verify the [latest][OVA] OVF file.
    - Import it.
    - Reconfigure network.
    - Start the VM and get IP.
    - Log into PMM UI.
    - (Optional) Change VM root password.
    - (Optional) Set up SSH.
    - (Optional) Set up static IP.

---

Most steps can be done with either a user interface or on the command line, but some steps can only be done in one or the other. Sections are labelled **UI** for user interface or **CLI** for command line instructions.

## Terminology

- *Host* is the desktop or server machine running the hypervisor.
- *Hypervisor* is software (e.g. [VirtualBox], [VMware]) that runs the guest OS as a virtual machine.
- *Guest* is the CentOS virtual machine that runs PMM Server.

## OVA file details

| Item          | Value
|---------------|-----------------------------------------------------------
| Download page | <https://www.percona.com/downloads/pmm2/{{release}}/ova>
| File name     | `pmm-server-{{release}}.ova`
| VM name       | `PMM2-Server-{{release_date}}-N` (`N`=build number)

## VM specifications

| Component         | Value
|-------------------|-------------------------------
| OS                | CentOS 7.9 (64-bit)
| CPU               | 1
| Base memory       | 4096 MB
| Disks             | LVM, 2 physical volumes
| Disk 1 (`sda`)    | VMDK (SCSI, 40 GB)
| Disk 2 (`sdb`)    | VMDK (SCSI, 400 GB)

## Users

| Default Username | Default password
|------------------|-----------------------
| `root`           | `percona`
| `admin`          | `admin`




