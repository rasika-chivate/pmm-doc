# VMware - Import OVA file

## OVA file downloaded from UI

1. Select *File* → *Import*.
2. Click *Choose file...*.
3. Navigate to the downloaded `.ova` file and select it.
4. Click *Open*.
5. Click *Continue*.
6. In the *Save as* dialog:

    a. (Optional) Change the directory or file name.

    b. Click *Save*.

7. Choose one of:

    - (Optional) Click *Finish*. This starts the virtual machine.
    - (Recommended) Click *Customize Settings*. This opens the VM's settings page without starting the machine.

## OVA file downloaded via CLI

1. Install [`ovftool`][OVFTool]. (You need to register.)
2. Import and convert the OVA file. (`ovftool` can't change CPU or memory settings during import but it can set the default interface.)

    Choose one of:

    - Download and import the OVA file.

        ```sh
        ovftool --name="PMM Server" --net:NAT=Wi-Fi \
        https://www.percona.com/downloads/pmm2/{{release}}/ova/pmm-server-{{release}}.ova \
        pmm-server-{{release}}.vmx
        ```

    - Import an already-downloaded OVA file.

        ```sh
        ovftool --name="PMM Server" --net:NAT=WiFi \
        pmm-server-{{release}}.ova \
        pmm-server.vmx
        ```

## Reconfigure interface

!!! note alert alert-primary ""
    When using the command line, the interface is remapped during import.

### Reconfigure with UI

1. If started, shut down the virtual machine.
2. In the VMware main window, select the imported virtual machine.
3. Click *Virtual Machine* → *Settings...*.
4. Click *Network Adapter*.
5. In the *Bridged Networking* section, select *Autodetect*.
6. Close the settings window.

### Start guest and get IP address from UI

1. In the VMware main window, select the imported virtual machine.
2. Click the play button <i class="uil uil-caret-right"></i> or select *Virtual Machine* → *Start Up*.
3. When the instance has been booted, note the IP address in the guest console.

### Start guest and get IP address from CLI

1. Start the virtual machine in GUI mode. (There's no way to redirect a VMware VM's console to the host.)

    ```sh
    vmrun -gu root -gp percona start \
    pmm-server.vmx gui
    ```

2. When the instance has been booted, note the IP address in the guest console.

3. (Optional) Stop and restart the instance in headless mode.

    ```sh
    vmrun stop pmm-server.vmx
    vmrun -gu root -gp percona start \
    pmm-server.vmx nogui
    ```