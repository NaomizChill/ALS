# \# Changelog

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

