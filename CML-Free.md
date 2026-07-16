# How to install Cisco Modeling Labs (CML) Free

**Download CML-Free** https://software.cisco.com/download/home/286193282/type/286326381/release/CML-Free  

| File Information                     | File Name                     |
|--------------------------------------|-------------------------------|
| CML Controller OVA                   | cml2_f_2.10.0-13_amd64-17.ova |
| Reference Platform ISO (refplat ISO) | refplat-20260409-free-iso.zip |

![images](./images/CML_vmware_file_open.png)  
![images](./images/CML_vmware_new_vm_name.png)  
![images](./images/CML_vmware_memory_size.png)  
![images](./images/CML_vmware_processor_cores.png)  
![images](./images/CML_vmware_expand_disk_capacity.png)  
![images](./images/CML_vmware_expand_disk_capacity_value.png)  
![images](./images/CML_vmware_expand_disk_capacity_successfully.png)  
Төмендегі суретте көрсетілгендей, **refplat-20260409-free.iso** файлды таңдау
![images](./images/CML_vmware_cdrom_use_iso_image_file.png)  
![images](./images/CML_vmware_network_adapter_vmnet1.png)  
немесе  
![images](./images/CML_vmware_network_adapter_vmnet0.png)  
![images](./images/CML_vmware_display.png)  
![images](./images/CML_vmware_power_vm.png)  
![images](./images/CML_deployment_configuration.png)  
![images](./images/CML_accept_eula.png)  
![images](./images/CML_brief_help.png)  
![images](./images/CML_deployment_type_standalone.png)  
![images](./images/CML_hostname.png)  
![images](./images/CML_username_password_sysadmin.png)  
![images](./images/CML_password_not_strong.png)  
![images](./images/CML_username_password_admin.png)  
![images](./images/CML_network_configuration_dhcp.png)  
![images](./images/CML_select_service_openssh.png)  
![images](./images/CML_confirm_configuration.png)  
![images](./images/CML_after_this_is_done.png)  
![images](./images/CML_copying_images_from_iso.png)  
![images](./images/CML_configuration_process.png)  
![images](./images/CML_console.png)  
![images](./images/CML_browser_cockpit_advanced.png)  
![images](./images/CML_browser_cockpit_advanced_risky.png)  
![images](./images/CML_browser_cockpit_web_ui.png)  
![images](./images/CML_browser_advanced.png)  
![images](./images/CML_browser_advanced_risky.png)  
![images](./images/CML_browser_web_ui.png)  
![images](./images/CML_vmware_cdrom_use_physical_drive.png)  
![images](./images/CML_vmware_devices_description.png)  

**7-қадам: Description**  

VMware Workstation -> Description  

```shell
CML Application User Account (CML Web UI)
https://ip_address
Username: admin
Password: P@s$w0rd

------------------------------------------

CML System Administrator Account (Cockpit)
https://ip_address:9090
Username: sysadmin
Password: P@s$w0rd
```

**8-қадам: I Copied It**

> C:\Users\student\Documents\Virtual Machines\CMLv2-2.10.0-Free  

`*.vmx` файлды ашып, төмендегі команданы енгіземіз!  
```shell
uuid.action = "create"
```

**9-қадам: Export to OVF**

![images](./images/vmware_export_to_ovf.png)  

Нәтижесінде төмендегідей 3 файл құрылады:  
  1) `*.mf`   - Manifest File
  2) `*.vmdk` - Virtual Machine Disk
  3) `*.ovf`  - Open Virtualization Format

**10-қадам: VMware OVF Tool арқылы OVA файл құру**

Download OVF Tool https://developer.broadcom.com/tools/open-virtualization-format-ovf-tool/latest  

Terminal (PowerShell) -> Run as administrator  
```shell
cd "C:\Program Files\VMware\VMware OVF Tool"
.\ovftool.exe --version
```

```shell
cd "$env:USERPROFILE\Documents\Virtual Machines\OVA"
```

```shell
dir
```

OVF to OVA file
```shell
& "C:\Program Files\VMware\VMware OVF Tool\ovftool.exe" `
"CMLv2-2.10.0-Free.ovf" `
"CMLv2-2.10.0-Free.ova"
```
The manifest validates  
Transfer Completed  
Completed successfully  
