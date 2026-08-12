# Лабораторная работа 1. Базовая настройка коммутатора 

### Задачи
Часть 1. Проверка конфигурации коммутатора по умолчанию

Часть 2. Создание сети и настройка основных параметров устройства
 -	Настройте базовые параметры коммутатора.
 -	Настройте IP-адрес для ПК.

Часть 3. Проверка сетевых подключений
 -	Отобразите конфигурацию устройства.
 -	Протестируйте сквозное соединение, отправив эхо-запрос.
 -	Протестируйте возможности удаленного управления с помощью Telnet


|  Устройство  |  Интерфейс  |  IP-адрес / префикс  |
|--------------|-------------|----------------------|
|      S1      |    VLAN 1   |     192.168.1.2/24   |
|      PC-A    |    NIC      |     192.168.1.10/24  |

### Часть 1. Проверка конфигурации коммутатора по умолчанию


```
Switch>
Switch>enable
Switch#show
Switch#show run
Switch#show running-config 
Building configuration...

Current configuration : 1080 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Switch
!
!
!
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
interface FastEthernet0/1
!
interface FastEthernet0/2
!
interface FastEthernet0/3
!
interface FastEthernet0/4
!
interface FastEthernet0/5
!
interface FastEthernet0/6
!
interface FastEthernet0/7
!
interface FastEthernet0/8
!
interface FastEthernet0/9
!
interface FastEthernet0/10
!
interface FastEthernet0/11
!
interface FastEthernet0/12
!
interface FastEthernet0/13
!
interface FastEthernet0/14
!
interface FastEthernet0/15
!
interface FastEthernet0/16
!
interface FastEthernet0/17
!
interface FastEthernet0/18
!
interface FastEthernet0/19
!
interface FastEthernet0/20
!
interface FastEthernet0/21
!
interface FastEthernet0/22
!
interface FastEthernet0/23
!
interface FastEthernet0/24
!
interface GigabitEthernet0/1
!
interface GigabitEthernet0/2
!
interface Vlan1
 no ip address
 shutdown
!
!
!
!
line con 0
!
line vty 0 4
 login
line vty 5 15
 login
!
!
!
!
end


Switch#
```

### Часть 2. Создание сети и настройка основных параметров устройства

####	Настройте базовые параметры коммутатора.
 - Произвели настройку базовых параметров.
  
    - Задано имя коммутатора.
    - Установлен пароль на enable.
    - Задан ip-адрес устройства согласно ТЗ.
    - Установлен пароль на line conscol и vty. Все пароли зашифрованы.
    - Прописана команда no shutdown для vlan 1
    - Включено подключение через telnet.
```
sw1(config-if)#do show run
Building configuration...

Current configuration : 1217 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
service password-encryption
!
hostname sw1
!
enable secret 5 $1$mERr$9cTjUIEqNGurQiFU.ZeCi1
!
!
!
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
interface FastEthernet0/1
!
interface FastEthernet0/2
!
interface FastEthernet0/3
!
interface FastEthernet0/4
!
interface FastEthernet0/5
!
interface FastEthernet0/6
!
interface FastEthernet0/7
!
interface FastEthernet0/8
!
interface FastEthernet0/9
!
interface FastEthernet0/10
!
interface FastEthernet0/11
!
interface FastEthernet0/12
!
interface FastEthernet0/13
!
interface FastEthernet0/14
!
interface FastEthernet0/15
!
interface FastEthernet0/16
!
interface FastEthernet0/17
!
interface FastEthernet0/18
!
interface FastEthernet0/19
!
interface FastEthernet0/20
!
interface FastEthernet0/21
!
interface FastEthernet0/22
!
interface FastEthernet0/23
!
interface FastEthernet0/24
!
interface GigabitEthernet0/1
!
interface GigabitEthernet0/2
!
interface Vlan1
 ip address 192.168.1.2 255.255.255.0
!
!
!
!
line con 0
 password 7 0822455D0A16
 login
!
line vty 0 4
 password 7 0822455D0A16
 login
 transport input telnet
line vty 5 15
 login
!
!
!
!
end
```
####	Настройте IP-адрес для ПК.

- Для ПК установлен IP-адрес согласно ТЗ.
