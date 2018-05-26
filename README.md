## Readme Layout
* [Ansible](#ansible) - software that automates software provisioning, configuration management, and application deployment
* [KVM](#kvm) - virtualization infrastructure for the Linux kernel that turns it into a hypervisor

## Getting Started

When working in the development environment you will need vagrant to create simulated kvm-host and python for ansible.

Install hombrew-cask, vagrant and it's dependencies
`brew tap caskroom/cask`

`brew cask install virtualbox vagrant vagrant-manager`

Install python3 and pipenv
`brew install python3 pipenv`

Upgrade pip and install virtualenv
`pip3 install --upgrade pip virtualenv`

Create the virtualenv
`virtualenv ~/.venv/pink`

Activate the virtualenv
`source ~/.venv/pink/bin/activate`

Install project dependencies
`pipenv install`

### Ansible

To get started working with ansible in development first run `vagrant up`

SSH into your vagrant box `vagrant ssh`


#### Ansible Vault
Create a password file

```
mkdir ~/.ansible ; \
echo "mypassword" >> ~/.ansible/.vault_pass.txt && \
chmod 0444 ~/.ansible/.vault_pass.txt
```

To generate the secret file, run `ansible-vault create vars/secret` from the project root.

The first prompt will create your vault password.

The second prompt will send you to a vim session, in that vim sesson input:
 
`ansible_sudo_pass: your-sudo-password`

## KVM
Widly supported across linux as the defacto virtualization infrastructure even AWS has transistioned from xen to KVM.

Inspecting our VM's
`virsh list --all`

This would give us a list of all vms.
```
 Id    Name                           State
----------------------------------------------------
 1     dnode0                         running
 2     bastion                        running
 -     ubuntu18_04_server             shut off
```

We can reboot machines with reboot `virsh reboot dnode0`
