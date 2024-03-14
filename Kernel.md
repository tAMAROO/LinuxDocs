# Kernel Documentation

## Fedora

### Switch Kernels:

```
uname -r - Checks what kernel is used
dnf list installed "kernel-*" - Checks what kernels are install, also can use dnf list kernel
sudo grubby --set-default /boot/vmlinuz-*.*.*-200.fc39.x86_64
reboot
```

### Delete old kernels:

You can list the currently installed kernels using rpm:

```
$ rpm -q kernel-core
kernel-core-5.6.8-300.fc32.x86_64
kernel-core-5.6.10-300.fc32.x86_64
kernel-core-5.6.11-300.fc32.x86_64
```

Then, you can remove one (not the one currently in use which you can find by running uname -a in a terminal) using dnf:

```
$ sudo dnf remove kernel-core-5.6.8-300.fc32
```

To only ever have two kernels installed, you need to change the value of installonly_limit in /etc/dnf/dnf.conf. It is 3 by default:
```
$ cat /etc/dnf/dnf.conf
[main]
gpgcheck=1
installonly_limit=3
clean_requirements_on_remove=True
best=False
skip_if_unavailable=True
```

You can do this using a terminal editor: nano/peco/vi/vim/emacs or sed:
```
$ sudo sed -i 's/installonly_limit=3/installonly_limit=2/' /etc/dnf/dnf.conf
```
```
$ cat /etc/dnf/dnf.conf
[main]
gpgcheck=1
installonly_limit=2
clean_requirements_on_remove=True
best=False
skip_if_unavailable=True
```
[https://discussion.fedoraproject.org/t/old-kernels-removal/77046/2]
