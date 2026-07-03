# How to install openEuler 24.03 LTS SP4

**Download VMware Desktop Hypervisor** https://drive.google.com/drive/folders/1xPeOKfdeOzGdEHJRhYktJThgL6-xjkHy?usp=sharing  

**Download openEuler 24.03 LTS SP4** https://www.openeuler.org/en/download/#openEuler%2024.03%20LTS%20SP4  

Table - **Minimum System Requirements**

| Component | Minimum Requirement |
|-----------|---------------------|
| Memory    | 4 GB                |
| Processor | 2 cores             |
| Storage   | 20 GB               |

login: **student**  
password: **Huawei@123**  

```shell
student@openEuler~$ groups student
student : student wheel
```

```shell
student@openEuler~$ sudo passwd student
password for user student: Huawei@123

New password: 123
Retype new password: 123
```

```shell
student@openEuler~$ sudo passwd root
New password: P@s$w0rd
Retype new password: P@s$w0rd
```

```shell
student@openEuler~$ ping -c2 google.com
```

```shell
student@openEuler~$ sudo dnf clean all
student@openEuler~$ sudo dnf makecache
```

```shell
student@openEuler~$ sudo dnf update -y
```

```shell
student@openEuler~$ sudo reboot
```

```shell
student@openEuler~$ sudo systemctl status sshd

student@openEuler~$ ip address
```

Configure Console Login Banner
```shell
student@openEuler~$ sudo vi /etc/issue
\S \l
Kernel \r

******************************************
Username: student
Password: 123
******************************************
Enter
Enter

:wq
```

Clear Bash History
```shell
student@openEuler~$ history

student@openEuler~$ ls -la
student@openEuler~$ cat /dev/null > ~/.bash_history
student@openEuler~$ history -c
```

Restart Guest
![images](./images/vmware_shutdown.png)
