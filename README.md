kernel-update

CentOS Linux release 8.5.2111

Проверяем ядро
[vagrant@kernel-update ~]$ uname -r
4.18.0-348.7.1.el8_5.x86_64

Обновляем ядро
yum --enablerepo=elrepo-kernel install kernel-ml

Installing:
 kernel-ml                         x86_64           6.7.9-1.el8.elrepo           elrepo-kernel          121 k
Installing dependencies:
 kernel-ml-core                    x86_64            6.7.9-1.el8.elrepo          elrepo-kernel          39 M
 kernel-ml-modules                 x86_64            6.7.9-1.el8.elrepo           elrepo-kernel          34 M

Далее настраиваем загрузчик.
Создаем файл конфигурации Grub  перезапускаем систему.
После перезагрузки проверяем ядро

uname -r
6.7.9-1.el8.elrepo.x86_64

Новое ядро установлено!!!


