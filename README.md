# vpn

## ДЗ


    Между двумя виртуалками поднять vpn в режимах

    tun;
    tap; Прочуствовать разницу.

    Поднять RAS на базе OpenVPN с клиентскими сертификатами, подключиться с локальной машины на виртуалку.

    3*. Самостоятельно изучить, поднять ocserv и подключиться с хоста к виртуалке


---

## Выполнение

tun; tap: tap - L2, tun - L3

Интерфейсы на сервере   

![](https://github.com/MaxOOOOON/vpn/blob/main/pictures/Screenshot_20211107_235815.png)  


Подключение к серверу на клиенте

    sudo openvpn /etc/openvpn/client/tun.ovpn &

либо 

    sudo openvpn /etc/openvpn/client/tap.ovpn &

![](https://github.com/MaxOOOOON/vpn/blob/main/pictures/Screenshot_20211107_235844.png)  


Проверка с локальной машины

    sudo openvpn host-profile/tap.ovpn &

![](https://github.com/MaxOOOOON/vpn/blob/main/pictures/Screenshot_20211107_235904.png)  
