# \# Changelog

# [v11.0.0] - 2026-05-17
Added

* Lab 15: OSPF dynamic routing — configuring dynamic routing between organization sites
* Packet Tracer topology file (15.pkt)
* OSPF process 1 configuration on all gateway routers with area 0 (BACKBONE)
* Router IDs assigned: `msk-donskaya-gw-1` → 10.128.254.1, `msk-q42-gw-1` → 10.128.254.2, `msk-hostel-gw-1` → 10.128.254.3, `sch-sochi-gw-1` → 10.128.254.4
* Network 10.0.0.0/8 announced into OSPF area 0 on all routers
* Direct point-to-point link between msk-q42 and sch-sochi via VLAN 7 (q42-sochi): subnet 10.128.255.8/30
* Subinterface `FastEthernet0/1.7` on `msk-q42-gw-1` (IP 10.128.255.9/30, description: sochi)
* Subinterface `FastEthernet0/0.7` on `sch-sochi-gw-1` (IP 10.128.255.10/30, description: q42)
* VLAN 7 (q42-sochi) created and enabled on `provider-irkolontirskiy-sw-1` and `sch-sochi-irkolontirskiy-sw-1`
* OSPF neighborship verification: `msk-donskaya-gw-1` — 2 neighbors (FULL/BDR), `msk-q42-gw-1` — 3 neighbors, `msk-hostel-gw-1` — 1 neighbor (FULL/DR), `sch-sochi-gw-1` — 2 neighbors
* Routing table analysis on all four gateway routers (24, 19, 14, 18 subnets respectively)
* ICMP simulation: packet path from admin laptop (Donskaya) to pc-sochi-1 (10.130.0.200) via primary route (VLAN 6) — 3 hops: 10.128.6.1 → 10.128.255.6 → 10.130.0.200
* Failover test: VLAN 6 disabled on `provider-irkolontirskiy-sw-1` — traffic rerouted via `msk-q42-gw-1` and VLAN 7 — 4 hops: 10.128.6.1 → 10.128.255.2 → 10.128.255.10 → 10.130.0.200
* Primary route restoration: VLAN 6 (sochi) recreated and brought up — OSPF reconverged to 3-hop path
* Lab report in Markdown, DOCX, and PDF formats
* Presentation in Markdown, HTML, and PDF formats
* Video recordings for lab execution and defense

Changed

* Updated repository structure for lab15
* Updated documentation and release links for GitHub and GitVerse

# \## \[v10.0.0] - 2026-05-09

# \### Added

# 

# \- Lab 14: Static routing — connecting remote subnets via provider network using static routes

# \- Packet Tracer topology file (14.pkt)

# \- VLAN 5 (q42) and VLAN 6 (sochi) on provider switch `provider-irkolontirskiy-sw-1`, trunk ports FastEthernet0/3 and FastEthernet0/4

# \- Subinterfaces FastEthernet0/1.5 and FastEthernet0/1.6 on central gateway `msk-donskaya-irkolontirskiy-gw-1`

# \- Static routes on central gateway: 10.129.0.0/16 via 10.128.255.2, 10.130.0.0/16 via 10.128.255.6

# \- Static default route on `msk-q42-irkolontirskiy-gw-1` via 10.128.255.1; subinterfaces f0/1.5, f0/0.201, f1/0.202

# \- Static route to hostel subnet 10.129.128.0/17 via 10.129.1.2 on `msk-q42-irkolontirskiy-gw-1`

# \- Static default route on `msk-hostel-irkolontirskiy-gw-1` via 10.129.1.1; VLAN 202 and VLAN 301 (hostel-main)

# \- Static default route on `sch-sochi-irkolontirskiy-gw-1` via 10.128.255.5; subinterfaces f0/0.6, f0/0.401, f0/0.402

# \- VLAN 201 (q42-main) on `msk-q42-irkolontirskiy-sw-1`, access port FastEthernet0/1

# \- VLAN 301 (hostel-main) on `msk-hostel-irkolontirskiy-sw-1`, access port FastEthernet0/1

# \- VLAN 401 (sochi-main) on `sch-sochi-irkolontirskiy-sw-1`, access port FastEthernet0/1

# \- Static IP configuration for workstations: 10.129.0.200 (q42), 10.129.128.200 (hostel), 10.130.0.200 (sochi); DNS 10.128.0.5

# \- NAT ACL extended with permits for hosts 10.129.0.200, 10.129.128.200, 10.130.0.200

# \- Connectivity verified via ping (0% loss to all remote stations), tracert, and show ip route on all gateways

# \- Lab report in Markdown, DOCX, and PDF formats

# \- Presentation in Markdown, HTML, and PDF formats

# \- Video recordings for lab execution and defense

# Changed

# 

# \- Updated repository structure for lab14

# \- Updated documentation and release links for GitHub and GitVerse

# \- Extended static routing to cover all distributed sites: q42, hostel, and Sochi branch

# 

# \## \[v9.0.0] - 2026-05-02

# \### Added

# \- Lab 13: Static routing preparation — connecting remote subnets via provider network

# \- Packet Tracer topology file (13.pkt)

# \- Subnet for Moscow district 42 (msk-q42): gateway `msk-q42-irkolontirskiy-gw-1`, switch `msk-q42-irkolontirskiy-sw-1`

# \- Subnet for Sochi branch (sch-sochi): gateway `sch-sochi-irkolontirskiy-gw-1`, switch `sch-sochi-irkolontirskiy-sw-1`

# \- Hostel subnet: gateway `msk-hostel-irkolontirskiy-gw-1`, switch `msk-hostel-irkolontirskiy-sw-1`

# \- Point-to-point links: 10.128.255.0/30 (link to q42), 10.128.255.4/30 (link to Sochi)

# \- IP address plan for new segments: 10.129.0.0/24 (q42 users), 10.130.0.0/24 (Sochi users), 10.130.1.0/24 (Sochi management)

# \- VLAN allocation for new segments: 201, 202 (q42), 401, 402 (Sochi)

# \- Updated L1, L2, L3 topology diagrams

# \- Physical map placement for all new devices and locations

# \- Initial configuration on all added devices: hostname, console/VTY passwords, login, enable secret, service password-encryption, user admin, domain name, RSA key generation, SSH access, write memory

# \- Lab report in Markdown, DOCX, and PDF formats

# \- Presentation in Markdown, HTML, and PDF formats

# \- Video recordings for lab execution and defense

# \### Changed

# \- Updated repository structure for lab13

# \- Updated documentation and release links for GitHub and GitVerse

# \- Extended corporate network topology to distributed multi-site architecture

# 

# \## \[v8.0.0] - 2026-05-02

# 

# \### Added

# \- Lab 12: NAT configuration — connecting local network to the Internet via provider

# \- Packet Tracer topology file (12.pkt)

# \- Initial configuration of provider-gw-1 and provider-sw-1

# \- External interface setup on msk-donskaya-irkolontirskiy-gw-1

# \- Default route configuration (0.0.0.0 0.0.0.0 198.51.100.1)

# \- NAT overload configuration with ACL nat-inet and pool main-pool (198.51.100.2–198.51.100.14)

# \- Static NAT rules for WEB (80), FTP (21), SMTP (25), POP3 (110), RDP (3389)

# \- Access verification for dk, departaments, adm, admin and other segments

# \- External server access checks (WEB, FTP, mail) from user-irkolontirskiy

# \- Lab report in Markdown, DOCX, and PDF formats

# \- Presentation in Markdown, HTML, and PDF formats

# \- Video recordings for lab execution and defense

# 

# \### Changed

# \- Updated repository structure for lab12

# \- Updated documentation and release links for GitHub and GitVerse

# 

# \### Fixed

# \- NAT inside/outside interface assignment on all subinterfaces

# \- Static NAT port forwarding verified for all published services

# 

# \## \[v7.0.0] - 2026-04-24

# 

# \### Added

# \- Lab 11: NAT planning — connecting local network to the Internet via provider

# \- Packet Tracer topology file (11.pkt)

# \- L1, L2, L3 network diagrams with physical and logical topologies

# \- VLAN table (management, servers, provider, dk, departments, adm, other)

# \- Port assignment table for all switches and routers

# \- Subnet plan table (10.128.x.x and 192.0.2.0/24 and 198.51.100.0/24)

# \- Lab report in Markdown, DOCX, and PDF formats

# \- Presentation in Markdown, HTML, and PDF formats

# \- Video recordings for lab execution and defense

# 

# \### Changed

# \- Extended network topology with provider and model Internet segments

# \- Added provider-irkolontirskiy-gw-1, provider-irkolontirskiy-sw-1, internet-irkolontirskiy-sw-1

# 

# \### Fixed

# \- DNS records configured for internal and external resources (esystem.pfur.ru, www.rudn.ru, www.yandex.ru etc.)

# \- IP configuration set on model Internet servers (192.0.2.0/24)

# 

# \## \[v6.0.0] - 2026-04-18

# 

# \### Added

# \- Lab 10: ACL configuration and traffic filtering in Packet Tracer

# \- Packet Tracer topology file (10.pkt)

# \- Lab report in Markdown, DOCX, and PDF formats

# \- Presentation in Markdown, HTML, and PDF formats

# \- Source archives for report and presentation

# \- Video recordings for lab execution and defense

# 

# \### Changed

# \- Repository structure aligned with course template

# \- Updated documentation and release links for GitHub and GitVerse

# 

# \### Fixed

# \- Access control rules for web, file, mail, DNS, FTP, Telnet, SMTP, POP3, SSH, and ICMP traffic

# 

# \## \[v5.0.0] - 2026-04-11

# 

# \### Added

# \- Lab 09: использование протокола STP и агрегирование каналов EtherChannel

# \- Топология лабораторной работы с резервными соединениями (09.pkt)

# \- Отчёт по лабораторной работе (report.md, report.docx, report.pdf)

# \- Презентация (presentation.md, presentation.html, presentation.pdf)

# \- Исследование ICMP-трафика до/после смены root bridge

# \- Настройка принудительного root bridge для VLAN 3 (msk-donskaya-sw-1)

# \- Включение PortFast на серверных портах sw-2 и sw-3

# \- Переход на Rapid PVST+ с проверкой отказоустойчивости

# \- EtherChannel между msk-donskaya-sw-1 и msk-donskaya-sw-4 (Fa0/20-23)

# 

# \### Changed

# \- Оптимизация топологии STP через центральный свитч sw-1

# \- Ускорение сходимости STP с Rapid PVST+ (2-6 сек вместо 30-50 сек)

# 

# \### Fixed

# \- Корректное формирование логического дерева STP

# \- Стабильная связность после реконвергенции

# 

# \## \[v4.0.0] - 2026-04-04

# 

# \### Added

# 

# \- Lab 08: настройка сетевых сервисов DNS и DHCP в Packet Tracer

# \- Топология лабораторной работы (08.pkt)

# \- Отчёт по лабораторной работе (report.md, report.docx, report.pdf)

# \- Презентация (presentation.md, presentation.html, presentation.pdf)

# \- Приведение структуры репозитория к шаблону курса (каталоги labs/lab0X, файл COURSE)

# 

# \## \[v3.0.0] - 2026-03-24

# 

# \### Added

# 

# \- Настройка физической рабочей области Packet Tracer

# \- Организация города Moscow, зданий Donskaya и Pavlovskaya

# \- Проверка сетевой связности между площадками

# \- Демонстрация влияния длины кабеля на связность сети

# \- Реализация решения с повторителями и оптоволоконным соединением

# \- Отчёт по лабораторной работе (report.docx, report.pdf)

# \- Презентация (presentation.html, presentation.pdf)

# 

# \## \[v2.0.0] - 2026-03-21

# 

# \### Added

# 

# \- Lab 06: Router-on-a-Stick inter-VLAN routing

# \- Packet Tracer simulation file (06.pkt)

# \- Lab report (report.md, report.docx, report.pdf)

# \- Presentation (presentation.md, presentation.html, presentation.pdf)

# 

# \## \[v1.0.0] - 2026-03-09

# 

# \### Added

# 

# \- Lab 05: VLAN configuration

# \- Packet Tracer simulation file (05.pkt)

# \- Lab report (report.md, report.docx, report.pdf)

# \- Presentation (presentation.md, presentation.html, presentation.pdf)

