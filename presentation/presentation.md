---
lang: ru-RU
title: Отчёт по лабораторной работе №4
subtitle: Первоначальное конфигурирование сети
author:
  - Илья Колонтырский
institute:
  - Российский университет дружбы народов, Москва, Россия
date: \today
toc: false
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
---

# Цели и задачи работы

## Цель лабораторной работы

Выполнить подготовительную работу по первоначальной настройке коммутаторов сети в Cisco Packet Tracer:
- собрать физическую топологию (L1),
- назначить имена устройств и IP-адреса управления,
- настроить базовые параметры доступа и безопасности,
- подготовить доступ к управлению (VTY/SSH).

## Задачи

- Разместить коммутаторы и конечные устройства согласно схеме L1.
- Соединить устройства через соответствующие интерфейсы.
- Настроить на коммутаторах интерфейс управления VLAN 2.
- Задать шлюз по умолчанию для управления.
- Настроить VTY/Console, enable secret, шифрование паролей, локального пользователя.
- Подготовить SSH (domain-name, RSA-ключи, transport input ssh).
- Сохранить конфигурацию.

# Физическая топология сети (L1)

## Размещение устройств и соединения

В Packet Tracer размещены и подключены:
- коммутаторы: msk-donskaya-irkolontirskiy-sw-1, sw-2, sw-3, sw-4, msk-pavlovskaya-irkolontirskiy-sw-1
- ПК: dk-pavlovskaya-irkolontirskiy-1, other-pavlovskaya-irkolontirskiy-1, dk-donskaya-irkolontirskiy-1, dep-donskaya-irkolontirskiy-1, adm-donskaya-irkolontirskiy-1, other-donskaya-irkolontirskiy-1
- серверы: web-irkolontirskiy, file-irkolontirskiy, mail-irkolontirskiy

Межкоммутаторные соединения выполнены магистральными линиями, конечные устройства подключены к access-портам.

## Схема L1

![Схема L1](01.png){ width=88% }

# Адресация управления (VLAN 2)

## Таблица IP-адресов управления

| Устройство                              | Интерфейс | IP-адрес     | Маска          | Шлюз       |
|------------------------------------------|-----------|--------------|----------------|------------|
| msk-donskaya-irkolontirskiy-sw-1         | Vlan2     | 10.128.1.2   | 255.255.255.0  | 10.128.1.1 |
| msk-donskaya-irkolontirskiy-sw-2         | Vlan2     | 10.128.1.3   | 255.255.255.0  | 10.128.1.1 |
| msk-donskaya-irkolontirskiy-sw-3         | Vlan2     | 10.128.1.4   | 255.255.255.0  | 10.128.1.1 |
| msk-donskaya-irkolontirskiy-sw-4         | Vlan2     | 10.128.1.5   | 255.255.255.0  | 10.128.1.1 |
| msk-pavlovskaya-irkolontirskiy-sw-1      | Vlan2     | 10.128.1.6   | 255.255.255.0  | 10.128.1.1 |

# Подтверждение настроек (CLI)

## msk-donskaya-irkolontirskiy-sw-1

![CLI sw-1](02.png){ width=88% }

## msk-donskaya-irkolontirskiy-sw-2

![CLI sw-2](03.png){ width=88% }

## msk-donskaya-irkolontirskiy-sw-3

![CLI sw-3](04.png){ width=88% }

## msk-donskaya-irkolontirskiy-sw-4

![CLI sw-4](05.png){ width=88% }

## msk-pavlovskaya-irkolontirskiy-sw-1

![CLI pavlovskaya-sw-1](06.png){ width=88% }

# Выводы

## Вывод

В Cisco Packet Tracer собрана физическая топология сети (L1) и выполнена базовая настройка всех коммутаторов.

На уровне управления настроен интерфейс VLAN 2 для каждого коммутатора, назначены IP-адреса из 10.128.1.0/24 и задан единый шлюз 10.128.1.1, что обеспечивает централизованный доступ к управлению.
