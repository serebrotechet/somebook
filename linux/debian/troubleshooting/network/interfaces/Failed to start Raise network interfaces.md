

## Чиним ошибку при загузке системы: Failed to start Raise network interfaces

Решение:

0. Идем в **/etc/network/interfaces.d/setup**
1. Меняем параметр **auto eth0** на **allow-hotplug eth0**
2. Перезагружаем систему.
