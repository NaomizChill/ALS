---
## Front matter
title: "Отчёт по лабораторной работе 4"
subtitle: "Первоначальное конфигурирование сети"
author: "Илья Колонтырский"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: IBM Plex Serif
romanfont: IBM Plex Serif
sansfont: IBM Plex Sans
monofont: IBM Plex Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9
mathfontoptions:
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Провести подготовительную работу по первоначальной настройке коммутаторов сети.

# Ход выполнения

В среде Cisco Packet Tracer была собрана физическая топология сети согласно схеме L1, после чего выполнена первоначальная (базовая) настройка всех коммутаторов по типовой конфигурации. Для каждого устройства назначено имя, настроен интерфейс управления VLAN 2, задан шлюз по умолчанию, включена защита паролей, создан локальный пользователь и подготовлен удалённый доступ по SSH.

## Размещение устройств и построение схемы L1

В логической рабочей области Packet Tracer размещены коммутаторы и оконечные устройства в соответствии со схемой L1.

Коммутаторы:
- msk-donskaya-irkolontirskiy-sw-1
- msk-donskaya-irkolontirskiy-sw-2
- msk-donskaya-irkolontirskiy-sw-3
- msk-donskaya-irkolontirskiy-sw-4
- msk-pavlovskaya-irkolontirskiy-sw-1

Рабочие станции:
- dk-pavlovskaya-irkolontirskiy-1
- other-pavlovskaya-irkolontirskiy-1
- dk-donskaya-irkolontirskiy-1
- dep-donskaya-irkolontirskiy-1
- adm-donskaya-irkolontirskiy-1
- other-donskaya-irkolontirskiy-1

Серверы:
- web-irkolontirskiy
- file-irkolontirskiy
- mail-irkolontirskiy

Коммутаторы соединены между собой магистральными линиями, конечные устройства подключены к access-портам соответствующих коммутаторов.

![Схема L1](01.png)

## Базовая настройка коммутаторов

Для каждого коммутатора выполнена типовая конфигурация.

Последовательность действий:

1. Переход в режим конфигурации и назначение имени устройства (hostname).
2. Настройка интерфейса управления:
   - interface vlan2
   - no shutdown
   - назначение IP-адреса из подсети 10.128.1.0/24
3. Настройка шлюза по умолчанию:
   - ip default-gateway 10.128.1.1
4. Настройка удалённого доступа:
   - line vty 0 4
   - password cisco
   - login
5. Настройка консольного доступа:
   - line console 0
   - password cisco
   - login
6. Включение защиты:
   - enable secret cisco
   - service password-encryption
   - username admin privilege 1 secret cisco
7. Подготовка SSH:
   - ip domain-name donskaya.rudn.edu
   - crypto key generate rsa
   - line vty 0 4
   - transport input ssh
8. Сохранение конфигурации:
   - write memory

## Таблица адресации управления (VLAN 2)

| Устройство                              | Интерфейс | IP-адрес       | Маска            | Шлюз          |
|------------------------------------------|-----------|---------------|------------------|---------------|
| msk-donskaya-irkolontirskiy-sw-1         | Vlan2     | 10.128.1.2    | 255.255.255.0    | 10.128.1.1    |
| msk-donskaya-irkolontirskiy-sw-2         | Vlan2     | 10.128.1.3    | 255.255.255.0    | 10.128.1.1    |
| msk-donskaya-irkolontirskiy-sw-3         | Vlan2     | 10.128.1.4    | 255.255.255.0    | 10.128.1.1    |
| msk-donskaya-irkolontirskiy-sw-4         | Vlan2     | 10.128.1.5    | 255.255.255.0    | 10.128.1.1    |
| msk-pavlovskaya-irkolontirskiy-sw-1      | Vlan2     | 10.128.1.6    | 255.255.255.0    | 10.128.1.1    |

## Подтверждение настройки (по данным CLI)

На всех коммутаторах:
- назначены уникальные имена устройств;
- активирован интерфейс Vlan2;
- назначены IP-адреса управления;
- задан шлюз по умолчанию 10.128.1.1;
- настроены линии VTY и Console с паролями;
- включено шифрование паролей;
- создан пользователь admin;
- настроен домен donskaya.rudn.edu;
- сгенерированы RSA-ключи;
- разрешён доступ по SSH;
- конфигурация сохранена в NVRAM.

![CLI sw-1](02.png)
![CLI sw-2](03.png)
![CLI sw-3](04.png)
![CLI sw-4](05.png)
![CLI pavlovskaya-sw-1](06.png)

# Вывод

В ходе выполнения работы в среде Cisco Packet Tracer была собрана физическая топология сети в соответствии со схемой L1 и выполнена базовая настройка всех коммутаторов.

На физическом уровне (L1) реализовано корректное подключение магистральных и пользовательских сегментов сети, а также серверной инфраструктуры. Межкоммутаторные соединения обеспечивают связанность всей сети, при этом конечные устройства подключены к соответствующим access-портам.

На уровне управления выполнена настройка интерфейса VLAN 2 для каждого коммутатора с назначением IP-адресов из подсети 10.128.1.0/24. Для всех устройств задан единый шлюз по умолчанию 10.128.1.1, что обеспечивает централизованный доступ к управлению.

В рамках базовой конфигурации реализованы:
- назначение уникальных имён устройств;
- настройка удалённого доступа через VTY-линии;
- настройка консольного доступа;
- включение шифрования паролей;
- создание локального пользователя;
- генерация RSA-ключей и активация доступа по SSH;
- сохранение конфигурации в энергонезависимой памяти.

В результате выполненных действий обеспечена готовность сетевой инфраструктуры к дальнейшей настройке уровней L2 и L3, а также к последующей сегментации сети и внедрению политики распределения VLAN и IP-адресов.

# Контрольные вопросы

**1. При помощи каких команд можно посмотреть конфигурацию сетевого оборудования?**  

Для просмотра текущей (активной) конфигурации используется команда:

- `show running-config`

Данная команда отображает конфигурацию, которая в настоящий момент загружена в оперативную память (RAM) и используется устройством.

Дополнительно могут применяться:
- `show running-config | section <имя>` — вывод определённого раздела конфигурации;
- `show ip interface brief` — краткая информация о состоянии интерфейсов;
- `show version` — сведения о версии IOS и параметрах оборудования.

Основной командой для просмотра текущей конфигурации является `show running-config`.

**2. При помощи каких команд можно посмотреть стартовый конфигурационный файл оборудования?**  

Для просмотра стартовой конфигурации, хранящейся в энергонезависимой памяти (NVRAM), используется команда:

- `show startup-config`

Этот файл загружается при перезагрузке устройства и становится текущей конфигурацией.

**3. При помощи каких команд можно экспортировать конфигурационный файл оборудования?**  

Экспорт конфигурации выполняется путём копирования файла на внешний сервер (TFTP, FTP, SCP и т.д.).

Основная команда:

- `copy running-config tftp`
- `copy startup-config tftp`

Также возможны варианты:
- `copy running-config ftp`
- `copy running-config scp`

В процессе выполнения указывается IP-адрес удалённого сервера и имя файла.

**4. При помощи каких команд можно импортировать конфигурационный файл оборудования?**  

Импорт выполняется обратной операцией — копированием конфигурационного файла с внешнего сервера на устройство.

Основные команды:

- `copy tftp running-config`
- `copy tftp startup-config`

Также возможны:
- `copy ftp running-config`
- `copy scp running-config`

После загрузки в `running-config` изменения применяются немедленно.  
Если конфигурация загружена в `startup-config`, для её активации требуется перезагрузка устройства (`reload`).