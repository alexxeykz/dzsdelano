При редактировании данного файла все выводится в столбик, при просмотре почему то все в строку и все сливается. 

Устанавливаем машину с помощью Vagrant
root@testvm:/home/kcentos# vagrant destroy
    kernel-update: Are you sure you want to destroy the 'kernel-update' VM? [y/N] y
==> kernel-update: Forcing shutdown of VM...
==> kernel-update: Destroying VM and associated drives...
root@testvm:/home/kcentos# vagrant up
Bringing machine 'kernel-update' up with 'virtualbox' provider...
==> kernel-update: Importing base box 'generic/centos8'...
==> kernel-update: Matching MAC address for NAT networking...
==> kernel-update: Setting the name of the VM: kcentos_kernel-update_1710362885080_91153
==> kernel-update: Clearing any previously set network interfaces...
==> kernel-update: Preparing network interfaces based on configuration...
    kernel-update: Adapter 1: nat
==> kernel-update: Forwarding ports...
    kernel-update: 80 (guest) => 8000 (host) (adapter 1)
    kernel-update: 22 (guest) => 2222 (host) (adapter 1)
==> kernel-update: Running 'pre-boot' VM customizations...
==> kernel-update: Booting VM...
==> kernel-update: Waiting for machine to boot. This may take a few minutes...
    kernel-update: SSH address: 127.0.0.1:2222
    kernel-update: SSH username: vagrant
    kernel-update: SSH auth method: private key
    kernel-update:
    kernel-update: Vagrant insecure key detected. Vagrant will automatically replace
    kernel-update: this with a newly generated keypair for better security.
    kernel-update:
    kernel-update: Inserting generated public key within guest...
    kernel-update: Removing insecure key from the guest if it's present...
    kernel-update: Key inserted! Disconnecting and reconnecting using new SSH key...
==> kernel-update: Machine booted and ready!
==> kernel-update: Checking for guest additions in VM...
    kernel-update: The guest additions on this VM do not match the installed version of
    kernel-update: VirtualBox! In most cases this is fine, but in rare cases it can
    kernel-update: prevent things such as shared folders from working properly. If you see
    kernel-update: shared folder errors, please make sure the guest additions within the
    kernel-update: virtual machine match the version of VirtualBox you have installed on
    kernel-update: your host and reload your VM.
    kernel-update:
    kernel-update: Guest Additions Version: 6.1.30
    kernel-update: VirtualBox Version: 7.0
==> kernel-update: Setting hostname...

Заходим из Vagrant на данную машину vagrant ssh
kernel-update

CentOS Linux release 8.5.2111

Проверяем ядро
[vagrant@kernel-update ~]$ uname -r
4.18.0-348.7.1.el8_5.x86_64

Обновляем ядро
yum --enablerepo=elrepo-kernel install kernel-ml

Installing:
 kernel-ml                         x86_64           6.7.9-1.el8.elrepo           elrepo-kernel
 
 Installing dependencies:
 kernel-ml-core                    x86_64            6.7.9-1.el8.elrepo          elrepo-kernel
 kernel-ml-modules                 x86_64            6.7.9-1.el8.elrepo           elrepo-kernel

Далее настраиваем загрузчик.
Создаем файл конфигурации Grub  перезапускаем систему.
После перезагрузки проверяем ядро

uname -r
6.7.9-1.el8.elrepo.x86_64

Новое ядро установлено!!!


