# Microwave Loader — готовые файлы

[Скачать MicrowaveLoader.exe](https://github.com/Rosecod337/MicrowaveLoader-updates/releases/latest/download/MicrowaveLoader.exe)

Версия **2026.10.19.7**, Windows x86, CS:GO Legacy. Достаточно одного EXE:
необходимые пакеты скачиваются автоматически без GitHub-входа и токена.
Исходники не публикуются.

## Использование

1. Выберите Neverlose или GameSense.
2. Выберите Stable либо Beta отдельным свитчем. Выбор сохраняется.
3. Выберите установленную игру: CS:GO Legacy или CS:GO в Steam (ветка `csgo_legacy`).
4. Нажмите «Запустить» или «Загрузить». Дополнительная галочка не нужна; модули проверяются автоматически.

Loader проверяет размеры, SHA256 и формат PE. Файлы устанавливаются рядом с
EXE; GameSense Beta — в `gamesense-beta/skeet.dll`. Стабильная `skeet.dll`
сохраняется. Кэш — `.microwave-downloads/packages` рядом с EXE.
Обновление Loader сохраняет резервную копию. После обновления снова нажмите запуск: игра автоматически не запускается.

Neverlose Stable использует `neverlose.dll`, Beta — `nlbeta.dll`; обе версии
используют сервер и `ent_fix.dll`. GameSense использует одну DLL без сервера
Neverlose. Современный CS2 не поддерживается. После ошибки загрузки полностью
перезапустите игру; не смешивайте разные версии в одном процессе.

Для приватного запуска без VAC нужны параметры Steam:

```text
-insecure -allow_third_party_software
```

## GameSense Beta

Отдельные настройки **VISUALS / Effects**: Viewmodel FOV/XYZ, Thirdperson distance, Aspect ratio, Ambient light, Model brightness, Fog, Show viewmodel in scope, Custom bloom, Custom exposure и Material remap. Общего Microwave section/master нет; используется штатное меню и прокрутка.

В **MISC / Miscellaneous**: Console filter, Buy bot и Kill message.

Buy bot: основное/дополнительное оружие и снаряжение, Ignore 16k limit, одна покупка по round_prestart после latency + 200 мс. Настройки и деньги перечитываются после задержки; выключение/отключение/смена уровня отменяют ожидание.

Kill message: Conversations / 1 / Custom, стили Normal / Toxic. Встроены все 809 диалогов исходной Lua — 305 Normal и 504 Toxic, 1583 строки: убийство, headshot, нож, граната, серия, смерть и реванш. Conversations используют паузы набора; Headshot only, No repeats и Delay относятся к режимам 1 / Custom. Team chat выбирает командный чат. Custom поддерживает `{name}`, `{weapon}`, `{hs}` и разделитель `|`; поле вмещает 63 позиции UTF-16, включая кириллицу и вставку Ctrl+V. Очередь сбрасывается при выключении, смене настроек или уровня. Сообщение ограничено 127 байтами с сохранением целых символов UTF-8.

Все 37 новых значений зарегистрированы в штатной системе конфигов; Custom-фразы сохраняются одним массивом. Пользователь подтвердил Save/Load первых 25 значений и работу scope/FPS (.19.3), Bloom/Exposure (.19.4). Новые Material remap, Buy bot и Kill message, их поля конфигов, автоматическая загрузка после перезапуска и FPS ещё требуют проверки в игре. Исходную Microwave Lua при проверке перенесённых функций оставьте выгруженной.

Material remap содержит все 372 пути из Lua для Mirage, Dust2, старой Dust2 и Overpass. Учитывает штатные Night mode/tint, применяет и возвращает изменения порциями с отменой очереди и проверкой владения. Один вызов движка при загрузке текстуры может превысить бюджет очереди; время кадра не гарантируется.

Offline: 882 проверки Kill message/данных/текстового поля, 91 прежняя проверка, x86 ABI вызовов и Release прошли; ранее прошли 790 проверок remap и 34 Buy bot. Это частичный перенос Lua в C++; полный перенос продолжается. Вылет при остановке сервера не заявлен исправленным.

Stable DLL сохранены без изменений из 2026.10.14.2. Подтверждение исправления Steam Overlay относится к стабильной GameSense DLL. При неизвестном профиле Overlay инициализация останавливается; журнал `skeet-crash-fix.log` находится рядом с DLL.

## Assets

- `MicrowaveLoader.exe` — Loader со свитчем Stable / Beta.
- `neverlose.zip`, `gamesense.zip` — стабильные пакеты.
- `neverlose-beta.zip`, `gamesense-beta.zip` — явно выбираемые тестовые пакеты.
- `manifest.json` — версии, размеры, SHA256 и признак Beta.
- `SHA256SUMS.txt` — контрольные суммы.

Серверные пакеты содержат штатную локальную пару TLS `certs/cert.pem` и
`certs/key.pem`. Эти файлы публичны и предназначены только для данного сервера.

[Релиз 2026.10.19.7](https://github.com/Rosecod337/MicrowaveLoader-updates/releases/tag/v2026.10.19.7).
