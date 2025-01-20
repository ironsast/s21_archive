## Part 1. Установка ОС

- ![Вывод версии OC](screenshots/1_version.png)
- Устанавливаем Ubuntu без графического интерфейса, выводим его версию командой `cat /etc/issue`

## Part 2. Создание пользователя

- ![Создание пользователя](screenshots/01_useradd.png)
- Создаем нового пользователя командой `sudo useradd -g groupname username`
- ![Вывод созданного пользователя](screenshots/2_adding-new-user.png)
- Выводим созданного пользователя на экран командой `cat /etc/passwd`

## Part 3. Настройка сети ОС

- ![Задание машине названия](screenshots/3_set-machine-name.png)
- Устанавливаем имя машины командой `sudo hostnamectl set-hostname user-1`
- ![Показываем имя машины](screenshots/4_checka-new-machine-name.png)
- Показываем имя машины командой `cat /etc/hostname`
- ![Устанавливаем временную зону](screenshots/5_set-and-check-new-datezone.png)
- Устанавливаем временную зону командой `sudo timedatectl set-timezone Europe/Moscow`
- Проверяем какая временная зона установлена командой `timedatectl`
- ![Названия сетевых интерфейсов](screenshots/6_network-interfaces.png)
- Выводим названия сетевых интерфейсов с помощью команды `ip -br link show`
- lo (сокр. loopback) - это интерфейс, который позволяет подключаться к самой машине и использовать хост в качестве клиента
- ![IP-адрес DHCP-сервера](screenshots/7_ip-from-dhcp.png)
- Получаем IP-адрес от DHCP-сервера командой `sudo dhclient -v enp0s3`
- DHCP (Dynamic Host Configuration Protocol) — это технология, которая автоматически присваивает компьютерам или другим устройствам IP-адрес при подключении к сети. 
- ![Содержимое таблицы маршрутизации](screenshots/8_check-ip-route.png)
- Проверяем IP шлюза командой `ip route`
- ![Внешний IP](screenshots/9_check-external-ip.png)
- Просматриваем внешний IP с помощью команды `curl ifconfig.me && echo "'`
- ![Внутренний IP](screenshots/10_check-internal-ip.png)
- Просматриваем внутренний IP с помощью команды `hostname -I`
- ![Меняем IP, GW, DNS](screenshots/11_set-ip-gw-n-dns.png)
- Редактируем вручную файл `/etc/netplan/00-installer-config.yaml` задавая статичные IP, GW и DNS и перезагружаем командой `reboot`
- ![Пингуем удаленные хосты](screenshots/12_pings.png)
- Пингуем удаленные хосты `1.1.1.1` и `ya.ru`  c помощью команды `ping`

## Part 4. Обновление ОС

- ![Обновление репозиториев](screenshots/13_sudo-apt-update.png)
- Обновляем репозитории командой `sudo apt update`
- ![Обновление ОС](screenshots/14_sudo-apt-upgrade-first.png)
- Обновляем систему командой `sudo apt upgrade`
- ![Проверка обновления ОС](screenshots/15_sudo-apt-upgrade-second.png)
- Повторно вводим команду `sudo apt upgrade` чтобы убедиться что система обновилась

## Part 5. Использование команды sudo

- ![Переключаемся на второго пользователя и меняем hostname ОС](screenshots/16_user-2-changing-hostname.png)
- С помощью команды `usermod -a -G sudo user-2` разрешаем пользователю выполнять команду `sudo` и меняем название машины от его лица.
- Команда `sudo` позволяет пользователям временно получить права администратора для выполнения команд, требующих высоких привилегий.

## Part 6. Установка и настройка службы времени

- ![Cинхронизация времени](screenshots/18_auto-set-dateformat.png)
- Для синхронизации времени используем команду `sudo timedatectl set-ntp 1`

## Part 7. Установка и использование текстовых редакторов

- ![Создаем текстовый файл в vim, записываем никнейм, сохрянем файл и выходим](screenshots/19_vim-insert.png)
- С помощью команды `vim test_vim.txt` создаем и открываем файл, нажимаем «i» чтобы переключиться на режим вставки и записываем свой никнейм, нажимаем «esc» чтобы переключиться на нормальный режим, вводим команду «:wq» для сохранения и выхода, нажимаем «enter»
- ![Создаем текстовый файл в nano, записываем никнейм, сохрянем файл и выходим](screenshots/20_nano-insert.png)
- С помощью команды `nano test_nano.txt` создаем и открываем файл, записываем свой никнейм, нажимаем «control-x y» для сохранения и выхода
- ![Создаем текстовый файл в emacs, записываем никнейм, сохрянем файл и выходим](screenshots/21_emacs-insert.png)
- С помощью команды `emacs test_emacs.txt` создаем и открываем файл, записываем свой никнейм, нажимаем «control-x control-c y» для сохранения и выхода
- ![Открываем текстовый файл в vim, записываем строку «21 School 21» и выходим без сохранения](screenshots/22_vim-without-save.png)
- С помощью команды `vim test_vim.txt` открываем файл, нажимаем «i» чтобы переключиться на режим вставки и записываем вместо никнейма строку «21 School 21», нажимаем «esc» чтобы переключиться на нормальный режим, вводим команду «:q!» для выхода без сохранения, нажимаем «enter»
- ![Открываем текстовый файл в NANO, записываем строку «21 School 21» и выходим без сохранения](screenshots/23_nano-without-save.png)
- С помощью команды `nano test_nano.txt` открываем файл, записываем вместо никнейма строку «21 School 21», нажимаем «control-x n» для выхода без сохранения
- ![Открываем текстовый файл в emacs, записываем строку «21 School 21» и выходим без сохранения](screenshots/24_emacs-without-save.png)
- С помощью команды `emacs test_emacs.txt` открываем файл, записываем вместо никнейма строку «21 School 21», нажимаем «control-x control-c n yes» для выхода без сохранения
- ![Открываем текстовый файл в vim, ищем подстроку](screenshots/25_vim-find-word.png)
- С помощью команды `vim test_vim.txt` открываем файл, нажимаем «/» чтобы начать поиск, после чего вводим подстроку
- ![Открываем текстовый файл в vim, заменяем подстроку](screenshots/26_vim-find-n-switch.png)
- С помощью команды `vim test_vim.txt` открываем файл, вводим «:s/», вводим подстроку которую хотим заменить, вводим «/», вводим подстроку на которую хотим заменить исходную подстроку, нажимаем «enter»
- ![Открываем текстовый файл в nano, ищем подстроку](screenshots/27_nano-find-word.png)
- С помощью команды `nano test_nano.txt` открываем файл, нажимаем «control-w» чтобы начать поиск, после чего вводим подстроку и нажимаем «enter»
- ![Открываем текстовый файл в nano, заменяем подстроку](screenshots/28_nano-find-n-switch.png)
- С помощью команды `nano test_nano.txt` открываем файл, нажимаем «control-w control-r», вводим подстроку которую хотим заменить, нажимаем «enter», вводим подстроку на которую хотим заменить исходную подстроку, нажимаем «enter», вводим «y»
- ![Открываем текстовый файл в emacs, ищем подстроку](screenshots/29_emacs-find-word.png)
- С помощью команды `emacs test_emacs.txt` открываем файл, нажимаем «control-s» чтобы начать поиск, после чего вводим подстроку
- ![Открываем текстовый файл в EMACS, заменяем подстроку](screenshots/30_emacs-find-n-switch.png)
- С помощью команды `emacs test_emacs.txt` открываем файл, нажимаем «option-x» чтобы ввести команду, после чего вводим replace-string и нажимаем «enter». Вводим подстроку которую хотим заменить, нажимаем «enter», вводим подстроку на которую хотим заменить, нажимаем «enter».

## Part 8. Установка и базовая настройка сервиса SSHD
- ![Установка OpenSSH](screenshots/31_install-open-ssh.png)
- Устанавливаем службу SSHd при помощи командыы `sudo apt install openssh-server`
- ![Добавление автостарта для службы](screenshots/32_autostart-for-ssh.png)
- Добавляем автостарт службы при запуске системы командой `sudo upate-rc.d ssh defaults`
- ![Включение службы](screenshots/33_ssh-enable.png)
- Включаем службу командой `sudo systemctl enable ssh`
- ![Старт службы](screenshots/34_ssh-start.png)
- Стартуем службу командой `sudo systemctl start ssh`
- ![Изменение порта](screenshots/35_changing-port-2022.png)
- Изменяем порт вручную командой `sudo nano /etc/ssh/sshd_config`
- ![Информация по процессу](screenshots/36_view-sshd-info.png)
- Смотрим информацию о процессе sshd командой `ps -FC sshd`. Флаг F выдает подробную информацию, флаг С выдает информацию по дочерним процессам
- ![Перезапуск SSHd](screenshots/37_restart-sshd.png)
- Перезапускаем службу командой `sudo systemctl restart sshd.service`
- ![Измененный порт](screenshots/38_netstat-info.png)
- Результат команды `netstat -tan`
- Флаг t - вывод TCP соединений; флаг а - вывод прослушиваемых и непрослушиваемых сокетов; флаг n - вывод в цифрах адреса, порта и имени пользователей
- Колонка Proto отображает протоколы, которые использует сокет. Колонка Recv-Q показывает количество байтов, которые еще не были скопированы пользовательской программой из сокета. Колонка Send-Q содержит информацию о количестве неподтвержденных байт, отправленных сокету. Колонка Local Address указывает адрес и порт локального сокета. Колонка Foreign Address показывает адрес и порт удаленного сокета. Колонка State отражает текущее состояние сокета. Значение 0.0.0.0 обозначает неопределенный адрес (любой).

## Part 9. Установка и использование утилит top, htop

- ![Использование команды top](screenshots/39_top-info.png)
- Uptime - 5 минут
- Количество авторизованных пользователей - 1
- Общая загрузка системы - 0.00, 0.04, 0.01
- Общее количество процессов - 119
- Загрузка CPU - 14.7%
- Загрузка памяти - 172.6
- Pid процесса, занимающего больше всего памяти - 1228
- Pid процесса, занимающего больше всего процессорного времени - 1228
- ![Сортировка по PID](screenshots/40_htop-sorted-by-pid.png)
- Сортировка по PID
- ![Сортировка по Percent_CPU](screenshots/41_htop-sorted-by-percent-cpu.png)
- Сортировка по Percent_CPU
- ![Сортировка по Percent MEM](screenshots/42_htop-sorted-by-percent-mem.png)
- Сортировка по Percent MEM
- ![Сортировака по TIME](screenshots/43-htop-sorted-by-time.png)
- Сортировка по TIME
- ![Фильтр по sshd](screenshots/44_sshd-filter.png)
- Фильтр по sshd
- ![Процесс syslog, найденный через поиск](screenshots/45_syslog-search.png)
- Процесс syslog, найденный через поиск
- ![Вывод hostname, clock и uptime](screenshots/46_adding-hostname-uptame-n-clock.png)
- Вывод hostname, clock и uptime

## Part 10. Использование утилиты fdisk

- ![Использование команды fdisk](screenshots/47_fdisk.png)
- Название жесткого диска VBOX HARDDISK
- Размер - 25 Gib, 26843545600 bytes
- 52428800 секторов
- Размер swap 2Gib

## Part 11. Использование утилиты df

- ![Использование команды df](screenshots/48_df.png)
- Размер раздела - 11758760 Килобайт
- Размер занятого пространства - 5179088 Килобайт
- Размер свободного пространства - 5960654 Килобайт
- Процент использования - 47%
- ![Использование команды df с флагами -Th](screenshots/49_df-Th.png)
- Размер раздела - 12 Гигабайт
- Размер занятого пространства - 5 Гигабайт
- Размер свободного пространства - 5.7 Гигабайт
- Процент использования - 47%
- Тип файловой системы для раздела - ext4

## Part 12. Использование утилиты du

- ![Использование команды du](screenshots/50_du.png)
- Запускаем команду `du`
- Выводим размер папок /home, /var, /var/log (в байтах, в человекочитаемом виде)
- флаг `h` для вывода в человеческом стиле
- флаг `b` для вывода в виде байтов
-![Вывод du -b -h /home](screenshots/51_du-home.png)
-![Вывод du -b /var](screenshots/52_du-b-var.png)
-![Вывод du -h /var](screenshots/53_du-h-var.png)
-![Вывод du -b /var/log](screenshots/02_du-b-var-lo.png)
-![Вывод du -b /var/log](screenshots/03_du-h-var-lo.png)
-![Вывод du -b /var/log/*](screenshots/54_du-b-var-log.png)
-![Вывод du -h /var/log/*](screenshots/55_du-h-var-log.png)

## Part 13. Установка и использование утилиты ncdu

- ![Использование команды ncdu /home](screenshots/56_ncdu-home.png)
- ![Использование команды ncdu /var](screenshots/57_ncdu-var.png)
- ![Использование команды ncdu /var/log](screenshots/58_ncdu-var-log.png)
- Делаем вывод команды `ncdu [dirname]`, в данном случае `/home`, `/var`, `/var/log`.

## Part 14. Работа с системными журналами

- ![Информация из /var/log/dmesg](screenshots/59_cat-var-log-dmesg.png)
- Вывод просмотра /var/log/dmesg
- ![Информация из /var/log/syslog](screenshots/60_cat-var-log-syslog.png)
- Вывод просмотра /var/log/syslog
- ![Время последней авторизации](screenshots/61_cat-var-log-auth.png)
- Время последней авторизации 19:16:19, имя пользователя ironsast
- ![Рестарт службы](screenshots/62_syslog-after-restart.png)
- Рестарт службы

## Part 15. Использование планировщика заданий CRON
- ![Редактируем список текущих заданий](screenshots/63_adding-uptime.png)
- crontab -e (редактировать файл)
- ![Список текущих заданий](screenshots/64_crontab-list.png)
- crontab -l (показать список задач)
- ![Состояние uptime](screenshots/65_uptime-output.png)
- Запускаем команду uptime через каждые 2 минуты при помощи команды `*/2 * * * * uptime`
- ![Список текущих заданий](screenshots/66_ITS-FINAL-CRONTABING.png)
- Удаляем все задания из планировщика заданий.
