<h1 align="center">
    <img src="http://s09.radikal.ru/i182/1610/5f/e56ed82e77f8t.jpg" height="25%" width="25%"/>
    <br/>
    SourceBans Material Admin
    <br/>
    New Plugin for SourceMod
</h1>

### [![GitHub license](https://img.shields.io/badge/license-GPLv3-blue.svg?style=flat-square)](https://github.com/SB-MaterialAdmin/NewServer/blob/master/LICENSE) [![GitHub forks](https://img.shields.io/github/forks/SB-MaterialAdmin/NewServer.svg?style=flat-square)](https://github.com/SB-MaterialAdmin/NewServer/network) [![GitHub stars](https://img.shields.io/github/stars/SB-MaterialAdmin/NewServer.svg?style=flat-square)](https://github.com/SB-MaterialAdmin/NewServer/stargazers) [![GitHub issues](https://img.shields.io/github/issues/SB-MaterialAdmin/NewServer.svg?style=flat-square)](https://github.com/SB-MaterialAdmin/NewServer/issues) [![Travis Build](https://travis-ci.org/SB-MaterialAdmin/NewServer.svg?branch=master)](https://travis-ci.org/SB-MaterialAdmin/NewServer)

### Ссылки
- [Скачать этот плагин](https://github.com/SB-MaterialAdmin/NewServer/archive/master.zip)
- [Ищете старый?](https://github.com/SB-MaterialAdmin/OldServer)
- [Веб-панель](https://github.com/SB-MaterialAdmin/Web)
- [FAQ](https://github.com/SB-MaterialAdmin/Web/wiki/FAQ)

### Внимание !!!
Удалите локальное бд **maDatabase** при обновление с 0.6.3 и ниже версий.
Для отключения или включения debug идём в файл materialadmin.inc и правим строку #define MADEBUG на 0 - выключено 1 - включено, заново компилируем все плагины.

### Описание
- В один плагин **materialadmin** включено:
  - Работа с админами
  - Работа с банами
  - Работа с мутами
  - Оффлайн бан
  - Массбан

### Установка
- Если использовались старые плагины:
  - Удалить старые плагины рефорка.
  - Изменить название секции в _/addons/sourcemod/configs/databases.cfg_ с **sourcebans** на **materialadmin**. Если в файле есть секция **sourcecomms**, можете её удалить.
- Если не использовались старые плагины:
  - Создать секцию в _/addons/sourcemod/configs/databases.cfg_ с данными от БД, и с именем **materialadmin**.
- Настроить конфиг в _/addons/sourcemod/configs/materialadmin/config.cfg_. **Не используйте старый конфиг**, в старом нет некоторых настроек.
- Если используется SourceMod версии 1.7, желательна перекомпиляция плагинов.

### О плагинах
| Наименование плагина | Что делает? |
|:--------------------:|-------------|
|**materialadmin**     |Сам плагин для выдачи банов, мутов. Своеобразное ядро.|
|**ma\_checker**       |Аналог **sb\_checker** из старых плагинов. Выводит кол-во банов у игроков админам при их заходе.|
|**ma\_basecomm**      |"Прослойка" между **materialadmin** и плагинами, которые требуют для работы стандартный **BaseComm** из поставки SourceMod.|
|**ma\_adminmenu**     |Переделанное стандартное меню Администратора SourceMod. В заголовке выводится время, если у администратора временная админка.|

### Команды
| Команда | Аргументы | Требуемый админ флаг | Что делает? |
|--------:|:---------:|:--------------------:|-------------|
|**ma\_off\_clear**|-|**ADMFLAG\_ROOT**|Очистка истории|
|**ma\_bekap\_clear**|-|**ADMFLAG\_ROOT**|Очистка бекапа|
|**ma\_reload**|-|**ADMFLAG\_RCON**|Перезагрузка меню и конфигов|
|**ma\_bd\_connect**|-|**ADMFLAG\_RCON**|Переподключение к БД|
|**ma\_rehashadm**|-|**ADMFLAG\_ROOT**|Обновить список админов|
|-|-|-|-|
|**sm\_ban**|<#userid\|#all\|#ct\|#t\|#blue\|#red> \<time\> [reason]|**ADMFLAG\_BAN**|Бан по SteamID|
|**sm\_banip**|<#userid\|#all\|#ct\|#t\|#blue\|#red> \<time\> [reason]|**ADMFLAG\_BAN**|Бан по IP|
|**sm\_addban**|<steamid\|ip> \<time\> [reason]|**ADMFLAG\_RCON**|Добавление бана по IP / SteamID|
|**sm\_unban**|<steamid\|ip> [reason]|**ADMFLAG\_UNBAN**|Разбан игрока по IP / SteamID|
|**sm\_gag**|<#userid\|#all\|#ct\|#t\|#blue\|#red> \<time\> [reason]|**ADMFLAG\_CHAT**|Отключение текстового чата|
|**sm\_mute**|<#userid\|#all\|#ct\|#t\|#blue\|#red> \<time\> [reason]|**ADMFLAG\_CHAT**|Отключение голосового чата|
|**sm\_silence**|<#userid\|#all\|#ct\|#t\|#blue\|#red> \<time\> [reason]|**ADMFLAG\_CHAT**|Отключение всего чата|
|**sm\_ungag**|<#userid\|#all\|#ct\|#t\|#blue\|#red> \<time\> [reason]|**ADMFLAG\_CHAT**|Включение текстового чата|
|**sm\_unmute**|<#userid\|#all\|#ct\|#t\|#blue\|#red> \<time\> [reason]|**ADMFLAG\_CHAT**|Включение голосового чата|
|**sm\_unsilence**|<#userid\|#all\|#ct\|#t\|#blue\|#red> \<time\> [reason]|**ADMFLAG\_CHAT**|Включение всего чата|
|-|-|-|-|
|**ma\_addadmin**|<#userid> \<immunity\> \<flag\> \<pass\>|**ADMFLAG\_ROOT**|Добавить Администратора|
|**ma\_addadminoff**|<name\|login> \<steam\> \<immunity\> \<flag\> \<pass\>|**ADMFLAG\_ROOT**|Добавить Администратора (**SteamID указывать в кавычках**)|
|**ma\_deladmin**|<#userid\|steam> \<type\>|**ADMFLAG\_ROOT**|Удалить Администратора (Типы: 0 - Полностью; 1 - Только с сервера) (**SteamID указывать в кавычках**)|

### Цвета для чата
| Игра | Цвет | # |
|:----:|:----:|:-:|
|**Все**|Жёлтый|#1|
|**CS:GO**|RED|#2|
|**Все**|Светло-зелёный|#3|
|**Все**|Зелёный|#4|
|**CS:GO**|LIME|#5|
|**CS:GO**|LIGHTGREEN|#6|
|**CS:GO**|LIGHTRED|#7|
|**OrangeBox** (CS:S / TF2)|HTML-цвет (вместо **FFFFFF** - Ваш цвет в HEX-варианте)|#7FFFFFF|
|**CS:GO**|GRAY|#8|
|**CS:GO**|LIGHTOLIVE|#9|
|**CS:GO**|OLIVE|#10|
|**CS:GO**|PURPLE|#OB|
|**CS:GO**|LIGHTBLUE|#OC|
|**CS:GO**|BLUE|#OE|

### Сортировка в меню Администратора
```
"materialadmin"
{
    "item"  "ma_target_online"
    "item"  "ma_target_offline"
    "item"  "ma_target_list"
    "item"  "ma_setting"
    "item"  "ma_setting_admin"
}
```

### Структура меню
```
Управление блокировками| -> Игроки на сервере| -> Игроки| -> Бан| -> По Стиму| -> Время| -> Причина
-----------------------|--------------------------------|-------| -> По Айпи| --> Время| -> Причина
-----------------------|--------------------------------| -> Мут| -> Отключить голосовой чат| -> Время| -> Причина
-----------------------|----------------------------------------| -> Отключить текстовый чат| -> Время| -> Причина
-----------------------|----------------------------------------| -> Отключить весь чат| ------> Время| -> Причина
-----------------------|----------------------------------------| -> Включить голосовой чат
-----------------------|----------------------------------------| -> Включить текстовый чат
-----------------------|----------------------------------------| -> Включить весь чат
-----------------------| -> Вышедшие игроки| -> Игроки| -> Бан| -> По Стиму| -> Время| -> Причина
-----------------------|------------------------------|--------| -> По Айпи| --> Время| -> Причина
-----------------------|------------------------------| --> Мут| -> Отключить голосовой чат| -> Время| -> Причина
-----------------------|---------------------------------------| -> Отключить текстовый чат| -> Время| -> Причина
-----------------------|---------------------------------------| -> Отключить весь чат| ------> Время| -> Причина
-----------------------|---------------------------------------| -> Включить голосовой чат
-----------------------|---------------------------------------| -> Включить текстовый чат
-----------------------|---------------------------------------| -> Включить весь чат
-----------------------| -> Наказанные игроки на сервере| -> Игроки| -> Показать| -> Информация
-----------------------|-------------------------------------------| -> Выполнить| -> Отключить голосовой чат| -> Время| -> Причина
-----------------------|---------------------------------------------------------| -> Отключить текстовый чат| -> Время| -> Причина
-----------------------|---------------------------------------------------------| -> Отключить весь чат| ------> Время| -> Причина
-----------------------|---------------------------------------------------------| -> Включить голосовой чат
-----------------------|---------------------------------------------------------| -> Включить текстовый чат
-----------------------|---------------------------------------------------------| -> Включить весь чат
-----------------------| -> Управление| -> Обновить список админов
-----------------------|--------------| -> Очистить оффлайн историю
-----------------------|--------------| -> Перезагрузить конфиг
-----------------------|--------------| -> Переподключится к бд
-----------------------| -> Управление аминами| -> Добавить админа| -> Игрок не админ| -> Флаг| -> далее дествия через чат
----------------------------------------------| -> Удалить админа| --> Игрок админ| ----> Полностью
----------------------------------------------------------------------------------| ----> Тока с этого сервера
```

### Пояснение для Администраторов
По-умолчанию, включен Debug-режим (плагин пишет всё в логи), пока плагин в Beta-тестировании. Логи плагина находятся в _/addons/sourcemod/logs/materialadmin/_. Если появились ошибки или недочёты, пишите на Discord-сервер или где можете, обязательно прикладывая логи плагина, и логи ошибок SourceMod (если возникли ошибки).

Могут быть проблемы с мутами, так как теперь 3 типа вместо 2, и если у игрока мут на чат и голосовой, то будет работать тока одно. 
Для нормальной работы нужно их удалить и через админ меню снова выдать.

**BaseComm** от SourceMod выгружается. Если у Вас есть плагины, которые используют его, используйте "затычку" **ma\_basecomm**. Учтите: муты не будут содержать полную информацию касательно причины, администратора, и т.д..

### Для скриптеров
Есть include-файл, его описание на русском.

```
Здесь была тонна текста касательно функций плагина для сторонних плагинов, но я их пока что не перенёс :<
```

### Работа над ошибками
|Текст ошибки|Решение|
|------------|-------|
|`Failed to retrieve groups from the database, Unknown column 'maxbantime'`|Выполнить запрос к Базе данных, где `sb` - Ваш префикс таблиц: ```ALTER TABLE `sb_srvgroups` ADD `maxbantime` INT NOT NULL default -1, ADD `maxmutetime` INT NOT NULL default -1;```|
