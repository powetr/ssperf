# ssperf
cli tool for mutual meathure network parameters via iperf
ssperf — это высокоэффективный Bash-скрипт для автоматизированного измерения двусторонней пропускной способности сети между локальным и удаленным узлами.

Основные возможности

Двусторонний тест: Автоматический последовательный замер Upload и Download.
Умная авторизация: Поддержка SSH-паролей (через sshpass) и SSH-ключей.
Авто-инсталляция: Проверка наличия iperf3 на удаленной стороне и предложение автоматической установки (apt/dnf).
Контроль версий: Сравнение версий iperf3 для предотвращения ошибок парсинга JSON.
Мультиязычность: Поддержка русского и английского интерфейсов (ключ -Lg).
Интеграция: Вывод в формате JSON для Zabbix и поддержка Syslog (локально/удаленно).

Для работы скрипта требуются: iperf3, sshpass, jq, bc.

# Ubuntu / Debian:
sudo apt update && sudo apt install -y iperf3 sshpass jq bc

# CentOS / RHEL:
sudo dnf install -y iperf3 sshpass jq bc

Примеры использования

Базовый TCP тест:
./ssperf -h 192.168.1.10 -u root -p 'P@ssword'

UDP тест 1 Гбит/с на 8 потоков (EN интерфейс):
./ssperf -h 1.2.3.4 -u admin -k ~/.ssh/id_rsa -m udp -b 1G -n 8 -Lg en

Запись результата в локальный системный лог:
./ssperf -h 192.168.1.10 -u root -p 'pass' -L

Вывод для Zabbix (JSON):
./ssperf -h 192.168.1.10 -u root -p 'pass' -z

ssperf is a high-efficiency Bash script for automated dual-way bandwidth measurement between local and remote hosts.

Key Features
Dual-way Test: Automatically performs sequential Upload and Download measurements.
Smart Auth: Supports SSH passwords (via sshpass) and SSH keys.
Auto-install: Checks for iperf3 on the remote side and offers automatic installation (apt/dnf).
Version Control: Compares iperf3 versions to prevent JSON parsing errors.
Bilingual: Supports Russian and English interfaces (via -Lg flag).
Integration: JSON output for Zabbix and Syslog support (local/remote).

Required tools: iperf3, sshpass, jq, bc.
# Ubuntu / Debian:
sudo apt update && sudo apt install -y iperf3 sshpass jq bc

# CentOS / RHEL:
sudo dnf install -y iperf3 sshpass jq bc

Usage Examples
Basic TCP test:
./ssperf -h 192.168.1.10 -u root -p 'P@ssword'

UDP 1Gbps test with 8 streams (English interface):
./ssperf -h 1.2.3.4 -u admin -k ~/.ssh/id_rsa -m udp -b 1G -n 8 -Lg en

Log results to local syslog:
./ssperf -h 192.168.1.10 -u root -p 'pass' -L
Zabbix Integration (JSON output):
./ssperf -h 192.168.1.10 -u root -p 'pass' -z
