# neuro_ansible
Our Ansible files

# How make a computer ready for ansible

```
dnf -y install ansible mc net-tools openssh-server openssh-clients passwdqc cracklib-dicts shadow-utils

systemctl enable sshd
systemctl start sshd

useradd -b /specialusers/ ansibleuser
passwd_value="PUT_A_PASSWORD_HERE"
echo ansibleuser:$passwd_value | chpasswd
echo "ansibleuser ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/ansible
```

# How to make the server ready

Once:
```
dnf -y install ansible mc net-tools openssh-server openssh-clients passwdqc cracklib-dicts shadow-utils sshpass

ssh-keygen
```

And then for every computer:

```
passwd_value="PUT_A_PASSWORD_HERE"
sshpass -p "$passwd_value" ssh-copy-id -o "StrictHostKeyChecking accept-new" ansibleuser@COMPUTERNAME
```

