# <img src="https://github.com/Lifailon/RSA/blob/rsa/Image/ico/RSA-Logo.ico" width="25" /> RSA (Remote Shadow Administrator)

[![PowerShell](https://github.com/Lifailon/RSA/blob/rsa/Image/Logo/PowerShell-Button.ico)](https://github.com/PowerShell/PowerShell) \
[![Telegram @kup57](https://github.com/Lifailon/RSA/blob/rsa/Image/Logo/Telegram-Button.ico)](https://t.me/kup57)
[![RSA](https://img.shields.io/github/v/release/lifailon/rsa)](https://github.com/Lifailon/RSA/releases)

- [💡 Описание](#-Описание)
- [📦 Модули](#-Модули)
- [📘 Функционал](#-Функционал)
- [🔔 Дополнения](#-Дополнения)

**[🚀 Скачать (RSA.exe)](https://github.com/Lifailon/RSA/releases)**

## 💡 Описание

Программа для подключения к текущим RDP-сессиям по средствам **Shadow-подключения**. Так же содержит набор модулей, направленного на автоматизацию удаленного администрирования и взаимодействия с ОС Windows.

Можно использовать как альтернативное средство для удаленного подключения, таким как Radmin или VNC, которые требуют установки программного обеспечения по модели клиент-сервер. **Используется 100% кода на PowerShell и Windows Forms (без использования Toolbox)**, не содержит зависимостей в виде модулей. Протестировано на Windows Server 2016-2019 DC и Windows 10 Pro, не зависит от локализации ОС.

## 📦 Модули

* **[Get-Query](https://github.com/Lifailon/Get-Query)** - используется для парсинга программы **query.exe с выводом в PSObject**, с целью отображения текущих сессий и запущенных пользовательских процессов на компьютере (версия 1.2).

* **[Get-Query-Network](https://github.com/Lifailon/Get-Query-Network)** - модуль для поиска пользователей в сети.

* **[Get-Invent](https://github.com/Lifailon/Get-Invent-SQLite)** - используется для сбора данных об оборудовании на удаленном компьютере с выводом развернутого отчета в HTML-файл (версия 1.1).

* **[RSA-Modules](https://github.com/Lifailon/RSA-Modules)** - сборник некоторых функций, которые я выделил в отдельные модули.

## 📘 Функционал

При выборе сервера и нажатии кнопки **Query** отображается список текущих пользователей в виде таблицы, предварительно **проверяется доступность хоста (ping) и WinRM а так же uptime с выводом в status bar**. Для изменения списка компьютеров в меню выбрать **File - List Change** (Ctrl+S), для обновления списка - **List Update** (Ctrl+R). При выборе пользователя, можно произвести четыре действия: **Connect (Shadow-подключение)** с возможностью запроса на подключение и без (последнее удобно настраивается через GPO), **отключение пользователя (выход из системы)**, **отображение списка запущенных процессов пользователя с возможность их завершения** (правкой кнопкой мыши по выбранному процессу - **Stop Process**) и **отправка набранного сообщения** всем пользователям на сервере или выбранному в таблице. Есть возможность заполнить список серверов **компьютерами AD (Ctrl+D)** а так же вывести список в формате таблицы (Ctrl+T) с возможность сортировки и взаимодействия с выбранным компьютером.

<a href="https://github.com/Lifailon/RSA/blob/rsa/Image/Screen/Interface-1.4.1.jpg"><img src="https://github.com/Lifailon/RSA/blob/rsa/Image/Screen/Interface-1.4.1.jpg" width="400"/></a>
<a href="https://github.com/Lifailon/RSA/blob/rsa/Image/Screen/Services.jpg"><img src="https://github.com/Lifailon/RSA/blob/rsa/Image/Screen/Services.jpg" width="400"/></a>
<a href="https://github.com/Lifailon/RSA/blob/rsa/Image/Screen/LD.jpg"><img src="https://github.com/Lifailon/RSA/blob/rsa/Image/Screen/LD.jpg" width="400"/></a>
<a href="https://github.com/Lifailon/RSA/blob/rsa/Image/Screen/Time%2BLic%2BUpdate.jpg"><img src="https://github.com/Lifailon/RSA/blob/rsa/Image/Screen/Time%2BLic%2BUpdate.jpg" width="400"/></a>

Для подключение к серверу через rdp используется mstsc с ключем /admin, что позволяет подключаться к RDSH-серверу минуя Broker. **Для аутентификации используется cmdkey**, после прохождения единоразовой аутентификации (File - Authentication), используется предварительная аутентификация на все сервера в списке и действует до закрытия программы, что **позволяет не хранить пароль администратора в коде, а так же хранилище ключей ОС (которые можно скомпрометировать)**.

## 🔔 Дополнения

* **Admin - Services** - выводит списка служб на локальном или удаленном компьютере с возможность их запуска/перезапуска и остановки.
* **Admin - All Remote User Process** - используется для отображения списка всех пользовательских процессов с возможность их остановки.
* **Admin & WMI - Software** - выводит список установленного программного обспечения с возможность его удаления
* **WMI - Windows Update** - вывода списка обновлений с дальнейшим поиском по **HotFixID в DISM Packages** и удалением.
* **Admin - SMB Open Files** - отображение списка используемых сетевых сесурсов пользователями в сети с возможность закрытия их сессии.
* **Admin - Get-Netstat** - вывод списка слушающих и установленных TCP-соединений с преобразованием имени удаленного хоста (nslookup) и используемого процесса.
* **Admin - Get-RemoteDNS** - используется для удаленного просмотра на DC (не требует установки модуля из состава RSAT) списка всех DNS зон и дочерних записей выбранной зоны с возможностью удаления выбранной записи.
* **Admin - GPUpdate** - обновление групповых политик на удаленном компьютере.
* **Admin - GPResult** - составление сводного отчёта по результатам групповых политик в формате HTML для указанного пользователя на выбранном хосте.
* **Power - Reboot & Power Off** - перезагрузка или выключение хоста с задержкой 60 секунд.
* **Power - Screen lock & Sleep mode** - включение/отключение блокировки экрана и спящего режима на удаленном компьютере.
* **Power - Get-ARP & Get-DHCP** - используются для поиска MAC-адреса выключенного компьютера с целью его включения с помощью **Wake-on-Lan**.
* **Event** - логи питания (Power) и пять журналов событий для анализа подключений/отключений сессий.
* **Broker** - автоматизация командлетов взаимодействия с RDSH-фермой.
* **WMI - Logical Disk & Memory** - выводит общий и доступный объём локических дисков и оперативной памяти.
* **WMI - Drivers** - отобразить список драйверов.
* **WMI - File Share** - список общедоступных ресурсов на хосте (директорий или принтеров).
* **WMI - Power RDP & Power NLA** - проверяет статус Remote Desktop Protocol и Network Level Authentication на удаленно хосте с возможность включения и отключения.
> **WMI - Setup** - установка программного обеспечения на удаленный компьютер. Через install-package (сейчас используется этот вариант) и два метода через WMI. В первом случае установка происходит не на всех серверах (не зависимо от использования версии TLS), в случае с wmi установка происходит из UNC-пути только на тот же сервер, где лежит msi-пакет (в т.ч. через invoke session с предварительной аутентификацией на удаленной машине, где директория доступна по пути через icm).

### Скрипты по синхронизации компьютерных часов (w32tm).
* Отображает текущее время на сервере и разницу с сервером источника (localhost).
* Узнать источник времени, а так же частоту и время последней синхронизации (последнее отображается в зависимости от языкового пакета на удаленной машине).
* Проверка сервера как источника времени.
* Изменить на удаленном сервере источник времени на ближайший DC (с ролью PDC) в подсети.
* Изменить на внешний источник времени (например: ru.pool.ntp.org).
* Незамедлительно синхронизировать время на удаленном сервере с источником.

### Скрипты по активации корпоративных лицензий в сети (KMS).
* Узнать редакцию и версию ОС, канал получения лицензии, тип ключа, статус активации и сервер лицензирования.
* Узнать адрес KMS-сервера в сети по srv-записи.
* GVLK-активатор. Содержит публичные ключи GVLK (Generic Volume License Key) с возможностью удаленной активации.
* Указать в ручную KMS-сервер (например, если KMS-сервер не опубликован в DNS).
* Запросить (обновить) лицензию с  KMS-сервера.
