# Microwave Loader — готовые файлы

[Скачать MicrowaveLoader.exe](https://github.com/Rosecod337/MicrowaveLoader-updates/releases/latest/download/MicrowaveLoader.exe)

Windows x86 loader для CS:GO Legacy. Пользователю достаточно одного EXE:
необходимые пакеты скачиваются автоматически, без GitHub-входа или токена.
Исходники не публикуются.

## Использование

1. Запустите EXE и выберите Neverlose либо GameSense · тест.
2. Выберите установленный Steam App 4465480 либо 730 с beta csgo_legacy.
3. Подтвердите, что другой чит не загружен, и нажмите запуск.

Loader скачивает актуальный пакет, проверяет размеры/SHA256/PE, затем готовит
запуск выбранной игры. Файлы хранятся в `%LOCALAPPDATA%\MicrowaveLoader\packages`.
Новую версию самого EXE Loader скачивает и устанавливает с резервной копией.

Neverlose: сервер и две DLL. GameSense: отдельная DLL без сервера Neverlose.
Современный CS2 не поддерживается. Не смешивайте два чита в одной сессии.
После ошибки загрузки полностью перезапустите игру.

Для приватного запуска без VAC нужны параметры Steam:

```text
-insecure -allow_third_party_software
```

## Состояние GameSense

**Тестовая сборка, известен вылет.** 14 октября 2026 пользователь подтвердил
падение свежего билда в новой сессии. В трёх Steam minidump одинаковый access
violation: `gameoverlayrenderer.dll + 0x5EB6D`, запись по нулевому указателю.
Корневая причина ещё не установлена и не исправлена. Перед загрузкой этого
режима показывается предупреждение. Изолированные тесты Loader не доказывают
стабильность чита в игре.

## Assets

- `MicrowaveLoader.exe` — лоадер.
- `neverlose.zip` — DLL, сервер и его штатные локальные TLS-файлы.
- `gamesense.zip` — тестовая DLL скита.
- `manifest.json` — версии, размеры и SHA256 для автоматических скачиваний.
- `SHA256SUMS.txt` — контрольные суммы.

[Все Releases](https://github.com/Rosecod337/MicrowaveLoader-updates/releases).