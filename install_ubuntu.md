# How to install Ubuntu Server 24.04.4 LTS

**Download VMware Desktop Hypervisor** https://drive.google.com/drive/folders/1xPeOKfdeOzGdEHJRhYktJThgL6-xjkHy?usp=sharing  

**Download Ubuntu Server** https://ubuntu.com/download/server  

Table - **System Requirements**

| Component | Minimum Requirement |
|-----------|---------------------|
| Memory    | 2 GB                |
| Processor | 2 cores             |
| Storage   | 20 GB               |


![images](./images/vmware_config_type_custom.png)  
![images](./images/vmware_create_blank_hard_disk.png)  
![images](./images/vmware_guest_os_ubuntu.png)  
![images](./images/vmware_vm_name_ubuntu.png)  
![images](./images/vmware_processor_cores.png)  
![images](./images/vmware_memory_size.png)  
![images](./images/vmware_network_connection.png)  
![images](./images/vmware_scsi_controller.png)  
![images](./images/vmware_virtual_disk_type.png)  
![images](./images/vmware_create_new_virtual_disk.png)  
![images](./images/vmware_virtual_disk_size_ubuntu.png)  
![images](./images/vmware_virtual_disk_file_name_ubuntu.png)  
![images](./images/vmware_customize_hardware_ubuntu.png)  
![images](./images/vmware_processor_virtualization_engine.png)  
![images](./images/vmware_cdrom_ubuntu.png)  
![images](./images/vmware_network_adapter.png)  
![images](./images/vmware_display.png)  

![images](./images/ubuntu_installation_process_language.png)  
![images](./images/ubuntu_without_updating.png)  
![images](./images/ubuntu_keyboard_configuration.png)  
![images](./images/ubuntu_installation_type.png)  
![images](./images/ubuntu_network_configuration.png)  
![images](./images/ubuntu_proxy_configuration.png)  
![images](./images/ubuntu_archive_mirror_configuration.png)  
![images](./images/ubuntu_storage_configuration.png)  
![images](./images/ubuntu_storage_editing_lv.png)  
![images](./images/ubuntu_storage_edited_lv.png)  
![images](./images/ubuntu_continue.png)  
![images](./images/ubuntu_profile_configuration.png)  
![images](./images/ubuntu_skip.png)  
![images](./images/ubuntu_openssh_configuration.png)  
![images](./images/ubuntu_feature.png)  
![images](./images/ubuntu_installation_complete.png)  
![images](./images/ubuntu_click_enter.png)  

**Shut Down Guest**  
![images](./images/vmware_shutdown_vm.png)  

**Hardware Device (RAM, CPU, Storage, NIC, Display)**  
![images](./images/ubuntu_hardware_devices.png)  

**1-қадам: Set the Root Password**

login: **student**  
password: **123**  

```shell
student@ubuntu:~$ groups student
```

```shell
student@ubuntu:~$ sudo passwd root
New password: P@s$w0rd
```

**2-қадам: Update and Upgrade**
```shell
student@ubuntu:~$ ping google.com -c2

student@ubuntu:~$ sudo apt update
student@ubuntu:~$ sudo apt upgrade -y
```

```shell
student@ubuntu:~$ reboot
```

**3-қадам: System Information**
```shell
student@ubuntu:~$ uname -sr
student@ubuntu:~$ lsb_release -a
```

**4-қадам: Verify SSH Connectivity**
```shell
student@ubuntu:~$ sudo systemctl status ssh

student@ubuntu:~$ ip address
```

**5-қадам: Configure Console Login Banner Message**

```shell
student@ubuntu:~$ sudo nano /etc/issue
\S \l
Kernel \r

************************
Username: student
Password: 123
************************
ENTER
ENTER

CTRL+O, ENTER, CTRL+X
CTRL+L
```
`\S` - OS name  
`\l` - TTY name  
`\r` - Kernel release  

```shell
student@ubuntu:~$ logout
```

**6-қадам: optional: true**

```shell
student@ubuntu:~$ sudo nano /etc/netplan/50-cloud-init.yaml
network:
  version: 2
  ethernets:
    ens32:
      dhcp4: true
      optional: true

CTRL+O, ENTER, CTRL+X
CTRL+L

student@ubuntu:~$ sudo netplan apply
```

**7-қадам: Clear Bash History**

```shell
student@ubuntu:~$ history

student@ubuntu:~$ ls -la
student@ubuntu:~$ cat /dev/null > ~/.bash_history
student@ubuntu:~$ history -c
```

**Shut Down Guest**  
![images](./images/vmware_shutdown_vm.png)  

**8-қадам: Description**  

VMware Workstation -> Description  

Username: student  
Password: 123  

Username: root  
Password: P@s$w0rd  

**9-қадам: I Copied It**

> C:\Users\student\Documents\Virtual Machines\ubuntu-24.04.4-LTS\  

`*.vmx` файлды ашып, төмендегі команданы енгіземіз!  
```shell
uuid.action = "create"
```

**10-қадам: Export to OVF**

![images](./images/vmware_export_to_ovf.png)  

Нәтижесінде төмендегідей 3 файл құрылады:  
  1) `*.mf`   - Manifest File
  2) `*.vmdk` - Virtual Machine Disk
  3) `*.ovf`  - Open Virtualization Format

**11-қадам: VMware OVF Tool арқылы OVA файл құру**

Download OVF Tool https://developer.broadcom.com/tools/open-virtualization-format-ovf-tool/latest  

Terminal (PowerShell) -> Run as administrator  
```shell
cd "C:\Program Files\VMware\VMware OVF Tool"
.\ovftool.exe --version
```

```shell
cd "$env:USERPROFILE\Documents\Virtual Machines\OVF_files"
```

```shell
dir
```
![images](./images/ubuntu_dir_ovf_files.png)

OVF to OVA file
```shell
& "C:\Program Files\VMware\VMware OVF Tool\ovftool.exe" `
"ubuntu-24.04.4-LTS.ovf" `
"ubuntu-24.04.4-LTS.ova"
```
The manifest validates  
Transfer Completed  
Completed successfully  

```shell
dir
```
![images](./images/ubuntu_dir_ova_files.png)

**12-қадам: Take Snapshot**  
  
Snapshot Manager -> Take Snapshot -> Name: initial image  
