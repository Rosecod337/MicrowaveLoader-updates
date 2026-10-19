# Microwave Loader — готовые файлы

[Скачать MicrowaveLoader.exe](https://github.com/Rosecod337/MicrowaveLoader-updates/releases/latest/download/MicrowaveLoader.exe)

Версия **2026.10.19.3**, Windows x86, CS:GO Legacy. Достаточно одного EXE:
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

Семь нативных настроек в **VISUALS / Effects**: Viewmodel FOV/XYZ,
Thirdperson distance, Aspect ratio, Ambient light, Model brightness, Fog и Show viewmodel in scope.
Настройки включаются отдельными галочками; параметры раскрываются под своей
галочкой. Общий selector Microwave section и мастер удалены; прокрутка штатная.
В MISC / Miscellaneous добавлен Console filter с возвратом con_filter_*.
Scope меняет только флаг скрытия модели оружия при прицеливании в проверенном кэше клиента и возвращает его при отключении. В .19.2 пользователь подтвердил эффект, но обнаружил критическое падение FPS, исчезающее после выключения только scope. В .19.3 убрана покадровая нагрузка обработчика: engine-only, максимум четыре обновления в секунду, bulk-чтение и линейная проверка ID, без VirtualQuery/GetModuleHandle на запись. Переключение галочки и защита записи сохранены. 66 offline-проверок и локальный benchmark прошли; игровой FPS новой сборки ещё требует подтверждения.
Это частичный перенос Lua в C++. Полный перенос ещё не завершён.
Сборка и офлайн-проверки пройдены; расположение контролов и работа Beta в игре
требуют проверки пользователем.

Stable DLL в этом релизе сохранены без изменений из 2026.10.14.2. Игровое
подтверждение исправления Steam Overlay от 14 октября относится к стабильной
GameSense DLL, а не к новой Beta. При неизвестном профиле Overlay инициализация
останавливается; журнал `skeet-crash-fix.log` находится рядом с DLL.

## Assets

- `MicrowaveLoader.exe` — Loader со свитчем Stable / Beta.
- `neverlose.zip`, `gamesense.zip` — стабильные пакеты.
- `neverlose-beta.zip`, `gamesense-beta.zip` — явно выбираемые тестовые пакеты.
- `manifest.json` — версии, размеры, SHA256 и признак Beta.
- `SHA256SUMS.txt` — контрольные суммы.

Серверные пакеты содержат штатную локальную пару TLS `certs/cert.pem` и
`certs/key.pem`. Эти файлы публичны и предназначены только для данного сервера.

[Релиз 2026.10.19.3](https://github.com/Rosecod337/MicrowaveLoader-updates/releases/tag/v2026.10.19.3).
