## Ubuntu autoinstall ISO generated with ansible
This ansible playbook downloads newest Ubuntu server 22.04 from official repo and generates cloud-init autoinstall ISO with ```user-data``` file that contains the specifications for installation. Then it can be flashed to usb to continue installation.
It is based on notthebee's [ansible-role-ubuntu_autoinstall](https://github.com/notthebee/ansible-role-ubuntu_autoinstall) which uses Ubuntu 20.04 LTS and has option to upload it to pikvm for even more automated installation. This one is playbook, although it's quite easy to convert this to role.

### Usage
First cone this repo

```
git clone https://github.com/K9H9/ubuntu-autoiso-ansible
cd ubuntu-autoiso-ansible
```
Now it's best time to modificate ```main.yml``` file in ```defaults/``` to your needs.

Then run the main playbook. Note that you have to use ```--ask-become``` flag to do some of the operations(installing packages etc.) since they are executed on your local machine and you won't probably have passwordless sudo. Also note that ansible has to be installed before. 

```
ansible-playbook main.yml --ask-become
```
Give it some time (it might take couple of minutes since it downloads ISO which is 1,5Gb) and then the generated autoinstall ISO can be found from created directory ```ubuntu-autoiso``` in current directory. Then just flash and plug it to machine you want to install Ubuntu and let it run. After installation it can be accessed with ssh with normal user.

Make sure to configure your server after the installation to use atleast different password and maybe different user also. 
