---
type: zettel
---

```meta-bind-button
label: Set next review
hidden: false
id: review
style: primary
actions:
  - type: command
    command: review-obsidian:future-review
  - type: input
    str: "next 7 days"
```

# Ansible management host

```bash
dnf install -y ansible-core sshpass

mkdir lab-ansible
cd lab-ansible

ssh-keygen -t rsa -b 4096 -C "ansible@lab"
mkdir .ssh
mv ~/.ssh/* .ssh/

ssh-agent bash
ssh-add .ssh/ansible_id_rsa

sudo su -
useradd ansible -m -c "Ansible" -s /bin/bash -G wheel
mkdir ~ansible/.ssh
cat .ssh/ansible_id_rsa.pub > ~ansible/.ssh/authorized_keys
chown -R ansible:ansible ~ansible/.ssh
chmod 640 ~ansible/.ssh/authorized_keys

ssh -i .ssh/ansible_id_rsa ansible@localhost

ssh-copy-id -i .ssh/ansible_id_rsa.pub ansible@x.x.x.x
```

