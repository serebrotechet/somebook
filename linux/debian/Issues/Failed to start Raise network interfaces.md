Ошибка при загузке системы - Failed to start Raise network interfaces

Решение:
Идем в /etc/network/interfaces.d/setup
Меняем auto eth0 на allow-hotplug eth0
Перезагружаем систему.

