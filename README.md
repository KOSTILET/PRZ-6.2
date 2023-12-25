# Практическое задание №6.2 Настройка протокола GRE
Выполнил: Костомахин Антон Алеесандровчи 
Группа: ББМО-02-23

# Общая структурная схема сети
![image](https://github.com/KOSTILET/PRZ-6.2/assets/64083435/e74c6e52-5df8-4e75-89ea-5f4cac021250)

![image](https://github.com/KOSTILET/PRZ-6.2/assets/64083435/68ff3be2-d914-4010-bb50-d11a8b68492b)

# Часть 1: Проверка подключения маршрутизатора
# Шаг 1: Определение IP-адреса порта S0/0/0 на маршрутизаторе RA.

```
show ip int br 
```
![image](https://github.com/KOSTILET/PRZ-6.2/assets/64083435/c227a8b5-05e3-404e-a378-4ebafe5b7469)

# Отправка эхо-запроса с RB на RA

```
ping 64.103.211.2
```
![image](https://github.com/KOSTILET/PRZ-6.2/assets/64083435/aa819582-b2a9-483d-939c-46b82a06ea09)

# Шаг 2: Определение IP-адреса на ПК А.
```
ipconfig
```
![image](https://github.com/KOSTILET/PRZ-6.2/assets/64083435/c88b897a-2996-4797-a580-7f33e3e51e96)

# Шаг 3: Отправка эхо-запроса до настройки туннеля GRE
```
ping 192.168.1.2
```
![image](https://github.com/KOSTILET/PRZ-6.2/assets/64083435/b70685cd-657b-4008-9b1b-16b25bb65f15)

# Часть 2: Настройка туннеля GRE
# Шаг 1: Настройка туннеля GRE на маршрутизаторе RA

```
enable

conf t

int tunnel 0

ip address 10.10.10.1 255.255.255.252

tunnel source s0/0/0

tunnel destination 209.165.122.2

tunnel mode gre ip
```
![image](https://github.com/KOSTILET/PRZ-6.2/assets/64083435/8dc7561a-e1ed-4317-87b8-95c4688e8316)

# Шаг 2: Настройка туннеля GRE на маршрутизаторе RB.
```
en

conf t

int tunnel 0

ip address 10.10.10.2 255.255.255.252

tunnel source s0/0/0

tunnel destination 64.103.211.2

tunnel mode gre ip

```
![image](https://github.com/KOSTILET/PRZ-6.2/assets/64083435/1a515d81-5a12-4883-a769-be0d79bb5204)

# Шаг 3: Настройте маршрут для частного IP-трафика.
```
conf t

ip route 192.168.2.0 255.255.255.0 10.10.10.2
```
![image](https://github.com/KOSTILET/PRZ-6.2/assets/64083435/df6ae6f4-3bdf-4c29-bcb6-d36ceefdc599)
```
no shutdown

exit

ip route 192.168.1.0 255.255.255.0 10.10.10.1
```
![image](https://github.com/KOSTILET/PRZ-6.2/assets/64083435/3eb7cbe4-dd6e-449e-bfc3-77b41f0594cb)

# Часть 3: Проверка подключения маршрутизатора
# Шаг 1: Отправка эхо-запроса с ПК B на ПК А после настройки GRE туннеля
![image](https://github.com/KOSTILET/PRZ-6.2/assets/64083435/ddea9192-f574-4563-ba96-c3af357f67e5)
# Шаг 2: Трассировка от ПК А до ПК В
![image](https://github.com/KOSTILET/PRZ-6.2/assets/64083435/ca5ad282-c06a-4e15-9332-97fc2127c6f7)
# Проверка правильности выполнения работы
![image](https://github.com/KOSTILET/PRZ-6.2/assets/64083435/2a0dd289-1f61-413c-bae7-dca1e1203b55)
![image](https://github.com/KOSTILET/PRZ-6.2/assets/64083435/e973b465-5201-4c6a-97d8-86df7583a40a)
