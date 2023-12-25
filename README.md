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

Отправка эхо-запроса с RB на RA

```
ping 64.103.211.2
```
![image](https://github.com/KOSTILET/PRZ-6.2/assets/64083435/aa819582-b2a9-483d-939c-46b82a06ea09)

