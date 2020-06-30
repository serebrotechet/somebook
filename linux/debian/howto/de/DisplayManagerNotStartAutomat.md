Проблема:После использования FluxBox или манипуляций с ним за root юзера,
появились проблемы с стартом машины,Display Manager не запускался,вместо него открывалась 
консоль.

Решение:
с помошю команды exec lightdm Display manager запускалсья 
но, при рестарте машины снова терминал
Решением проблемы стало изминения RunLevel'a на 5 
У меня было 3 
С помошю команды init 1-6 можно проверить какой вам RunLevel подходит
Шаги:
systemctl get-default #Current level check 
multi-user.target #output 
systemctl list-units --type=target --all#ввывод всех доступных целей 
systemctl set-default graphical.target #выбор нужой цели,в данном случае RunLevel 5 
systemctl get-default # Проверяем если изменилось 
reboot