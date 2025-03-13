# Linux DO Part 1

## Part 1

- На рисунке ниже показана версия убунту

![Рисунок 1_1 - Версия убунту](./devops_pics/Part1_1.png)

## Part 2

- На рисунке ниже показаны команды для создания пользователя ali, добавления в группу adm

![Рисунок 2_1](./devops_pics/Part2_1.png)

- На рисунке ниже показан результат команды cat /etc/passwd

![Рисунок 2_2](./devops_pics/Part2_2.png)

- ali добавлен в группу adm:

![Рисунок 2_3](./devops_pics/Part2_3.png)

## Part 3

- Задаем название машины вида user-1: hostnamectl set-hostname user-1
- Рестартим систему: systemctl restart systemd-hostnamed

- Выводим название системы:

![Рисунок 3_1](./devops_pics/Part3_1.png)

- Меняем временную зону:

![Рисунок 3_2](./devops_pics/Part3_2.png)

- Выводим список сетевых интерфейсов:

![Рисунок 3_3](devops_pics/Part3_3.png)

- lo (loopback device) – виртуальный интерфейс, присутствующий по умолчанию в любом Linux. Он используется для отладки сетевых программ и запуска серверных приложений на локальной машине. С этим интерфейсом всегда связан адрес 127.0.0.1. У него есть dns-имя – localhost. Посмотреть привязку можно в файле /etc/hosts.

- sudo apt install isc-dhcp-server - производим установку DHCP-сервера
- sudo apt install net-tools - для ifconfig
- Используя консольную команду получить ip адрес устройства, на котором вы работаете, от DHCP сервера:

![Pic 3_4](devops_pics/Part3_4.png)

- Dynamic Host Configuration Protocol (DHCP) — это протокол клиент/сервер, который автоматически предоставляет хост Интернет-протокола (IP) с его IP-адресом и другой соответствующей информацией о конфигурации, такой как маска подсети и шлюз по умолчанию.

- Определи и выведи на экран внешний ip-адрес шлюза (ip)

![Pic 3_5](devops_pics/Part3_5.png)

- Внутренний IP-адрес шлюза, он же ip-адрес по умолчанию (gw):

![Pic 3_6](devops_pics/Part3_6.png)

- Задай статичные (заданные вручную, а не полученные от DHCP-сервера) настройки ip, gw, dns (используй публичный DNS-серверы, например 1.1.1.1 или 8.8.8.8).
- sudo nano /etc/netplan/00-installer-config.yaml
- Вот изменения в файле:

![Pic 3_7](devops_pics/Part3_7.png)

- sudo netplan apply

- Результат пингов

![Pic 3_8](devops_pics/Part3_8.png)

## Part 4

- Обнови системные пакеты до последней на момент выполнения задания версии.

- sudo apt update && sudo apt upgrade

![Pic 4_1](devops_pics/Part4_1.png)

## Part 5

- Команда sudo ( substitute user and do, подменить пользователя и выполнить ) позволяет строго определенным пользователям выполнять указанные программы с административными привилегиями без ввода пароля суперпользователя root. Если быть точнее, то команда sudo позволяет выполнять программы от имени любого пользователя, но, если идентификатор или имя этого пользователя не указаны, то предполагается выполнение от имени суперпользователя root. Таким образом, использование sudo позволяет выполнять привилегированные команды обычным пользователям без необходимости ввода пароля суперпользователя root.

- sudo usermod -aG sudo ali
- Скрин с измененным hostname:

![Pic5_1](devops_pics/Part5_1.png)

## Part 6

- Вывод следующей команды должен содержать NTPSynchronized=yes:
- timedatectl show

![Pic 6_1](devops_pics/Part6_1.png)

## Part 7

- Используя каждый из трех выбранных редакторов, создай файл test_X.txt, где X — название редактора, в котором создан файл. Напиши в нём свой никнейм, закрой файл с сохранением изменений.

- Vim:

![Pic 7_vim1](devops_pics/Part7_vim1.png)

- Выход с сохранением:
- :wq

- Nano:

![nano1](devops_pics/Part7_nano1.png)

- Выход с сохранением:
- ctrl+x, y

- MCEdit:

![mc1](devops_pics/Part7_mc1.png)

- Выход с сохранением:
- f2, f10

- Используя каждый из трех выбранных редакторов, открой файл на редактирование, отредактируй файл, заменив никнейм на строку «21 School 21», закрой файл без сохранения изменений.

- Vim:

![Pic 7_vim2](devops_pics/Part7_vim2.png)

- Выход без сохранения:
- :q!

- Nano:

![nano2](devops_pics/Part7_nano2.png)

- Выход без сохранения:
- ctrl+x, n

- MCEdit:

![mc2](devops_pics/Part7_mc2.png)

- Выход без сохранения:
- f10, No

- Используя каждый из трех выбранных редакторов, отредактируй файл ещё раз (по аналогии с предыдущим пунктом), а затем освой функции поиска по содержимому файла (слово) и замены слова на любое другое.

- Vim (Команды на картинках):

![Pic 7_vim3](devops_pics/Part7_vim3.png)

![Pic 7_vim4](devops_pics/Part7_vim4.png)

- Nano:
- Поиск: ctrl+w

![Alt text](devops_pics/Part7_nano3.png)

- Замена: ctrl+\

![Alt text](devops_pics/Part7_nano4.png)

- MCEdit:
- Поиск: f7

![mc3](devops_pics/Part7_mc3.png)

- Замена: f4

![mc4](devops_pics/Part7_mc4.png)

## Part 8

- sudo apt install openssh-server

- Добавить автозапуск:

![Alt text](devops_pics/Part8_1.png)

- Перенастрой службу SSHd на порт 2022:
- sudo vim /etc/ssh/sshd_config

![Alt text](devops_pics/Part8_2.png)

- Используя команду ps, покажи наличие процесса sshd. Для этого к команде нужно подобрать ключи.

- ps aux | grep sshd

![Alt text](devops_pics/Part8_3.png)

- Ps позволяет отображать и управлять процессами в операционной системе. Она предоставляет информацию о работающих процессах и позволяет мониторить их состояние.

- ps aux:
- Опция a указывает ps вывести на дисплей процессы всех пользователей, за исключением тех процессов, которые не связаны с терминалом и процессами группы лидеров.
- В u — подставки для ориентированных на пользователя формате, который обеспечивает подробную информацию о процессах.
- Опция x в ps перечисляет процессы без управляющего терминала. В основном это процессы, которые запускаются во время загрузки и работают в фоновом режиме.

- netstat -tan:

![Alt text](devops_pics/Part8_4.png)

-tan:

- t-по протоколу TCP

- a-Отображение всех подключений и ожидающих портов.

- n- Отображение адресов и номеров портов в числовом формате.

- Cтолбцы:

- Recv-Q -количество запросов в очередях на приём на данном узле/компьютере

- Send-Q -количество запросов в очередях на отправку на данном узле/компьютере

- Local Address - адрес и номер локального конца сокета

- Foreign Address - адрес и номер порта удаленного порта сокета

- State - состояние сокета

- Если в качестве адреса отображается 0.0.0.0 , то это означает - "любой адрес", т. е в соединении могут использоваться все IP-адреса существующие на данном компьютере.

## Part 9

- top:
- uptime:

![Alt text](devops_pics/Part9_1.png)

- авторизованные пользователи:

![Alt text](devops_pics/Part9_2.png)

- средняя загрузка:

![Alt text](devops_pics/Part9_3.png)

- Общее кол-во процессов

![Alt text](devops_pics/Part9_4.png)

- загрузку cpu

![Alt text](devops_pics/Part9_5.png)

- загрузку памяти

![Alt text](devops_pics/Part9_6.png)

- pid процесса занимающего больше всего памяти

- shift + m для сортировки по памяти:

![Alt text](devops_pics/Part9_7.png)

- pid процесса, занимающего больше всего процессорного времени
- shift + p для сортировки по процессорному времени

![Alt text](devops_pics/Part9_8.png)

- HTOP:

- Сортировка по:
- pid

![Alt text](devops_pics/Part9_9.png)

- percent_cpu

![Alt text](devops_pics/Part9_10.png)

- percent mem

![Alt text](devops_pics/Part9_11.png)

- time

![Alt text](devops_pics/Part9_12.png)

- Отфильтрованному для процесса sshd

![Alt text](devops_pics/Part9_13.png)

- с процессом syslog, найденным, используя поиск

![Alt text](devops_pics/Part9_14.png)

- clock, hostname, uptime

![Alt text](devops_pics/Part9_15.png)

## Part 10

![Alt text](devops_pics/10_1.png)

- Название: ubuntu--vg-ubuntu--lv
- Размер: 10 гб
- Секторы: 20971520
- Swap:

![Alt text](devops_pics/10_2.png)

## Part 11

- df:

![Alt text](devops_pics/11_1.png)

- На картинке выделена информация о корневом разделе, где:
- размер раздела - 10218772
- размер занятого пространства - 2792984
- размер свободного пространства - 6885116
- процент использования - 29%
- единица измерения - килобайты

- df -Th:

![Alt text](devops_pics/11_2.png)

- На картинке выделена информация о корневом разделе, где:
- размер раздела - 9.8G
- размер занятого пространства - 2.7G
- размер свободного пространства - 6.6G
- процент использования - 29%
- Tип файловой системы для раздела-ext4


## Part 12

- Читабельный вывод: du -h

- размер /home: du -h /home

![Alt text](devops_pics/12_1.png)

- /var: du -h /var

![Alt text](devops_pics/12_2.png)

- /var/log: du -h /var/log

![Alt text](devops_pics/12_3.png)

- sudo du -h /var/log/*:

![Alt text](devops_pics/12_4.png)

![Alt text](devops_pics/12_5.png)

## Part 13

- размер home:

![Alt text](devops_pics/13_1.png)

- размер /var:

![Alt text](devops_pics/13_2.png)

- /var/log:

![Alt text](devops_pics/13_3.png)

## Part 14

- Последняя успешная авторизация:
- grep "Accepted" /var/log/auth.log | tail -n 1

![Alt text](devops_pics/14_1.png)

- sudo systemctl restart sshd

![Alt text](devops_pics/14_2.png)

## Part 15

- Используя планировщик заданий, запусти команду uptime через каждые 2 минуты:

![Alt text](devops_pics/15_1.png)

- Строчки о выполнении:

![Alt text](devops_pics/15_2.png)

- Выведи на экран список текущих заданий для CRON:

![Alt text](devops_pics/15_3.png)

- Удали все задания из планировщика заданий:
- crontab -r

![Alt text](devops_pics/15_4.png)