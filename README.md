# anicli-ru

___
Скрипт для поиска и просмотра аниме из терминала с русской озвучкой или субтитрами для linux систем, 
написанный на python.

> !!! Этот проект в стадии разработки, возможны (будут точно) баги и ошибки

https://github.com/vypivshiy/ani-cli-ru/assets/59173419/bf7e78bd-cdd1-4871-a5b3-f48e6ed7ec28

## Установка

**Рекомендуется использовать pipx**

```shell
pipx install -U git+https://github.com/vypivshiy/ani-cli-ru.git@dev 
```
```shell
Поддерживаемые плееры
- mpv
- vlc (мало тестов)
```

## Опционально

Если вы будете использовать плеер без поддержки настройки http заголовков - рекомендуется 
дополнительно установить `ffmpeg` для перенаправления видео потока.


## Usage:
```shell
anicli-ru
```
Ключи запуска
```shell
-s --source - выбор источника. По умолчанию "animego"
-q --quality - минимально выводимое разрешение видео. Доступны: 0, 144, 240, 360, 480, 720, 1080. По умолчанию 0
  Например, если вы установили 1080 и такое видео отсутстует - выведет максимально допустимое
--ffmpeg - использовать ffmpeg бекенд для перенаправления видеопотока в видеоплеер
-p --player - какой видеоплеер использовать. доступны "vlc", "mpv". По умолчанию "mpv"
```

---
Отличия от старой версии:

- Клиент основан на prompt-toolkit, реализована надстройка [eggella](https://github.com/vypivshiy/eggella) - 
архитектура схожа с flask и фреймворками чат ботов (aiogram, discord.py, ...))
- [Api интерфейс парсера](https://github.com/vypivshiy/anicli-api/tree/dev) и Cli клиента 
разделены в отдельные репозитории. Также, API интерфейс поддерживает asyncio!
- http клиент заменен с `requests` на `httpx` с включенным по умолчанию **http2** протоколом.
- парсеры работают в связке `httpx`, `parsel`, `chompjs` вместо одних регулярных выражений (как в yt-dlp)
- Использует экспериментальную обёртку [scrape-schema](https://github.com/vypivshiy/scrape-schema) для 
повышения ремонтопригодности, консистентности, читабельности и переиспользуемости кода 
~~если вы знаете что такое css, xpath серекторы и parsel~~.



## Roadmap
- [x] минимальная реализация
- [x] выбор источника
- [x] ffmpeg адаптер (не работает вывод title)
- [ ] конфигурация http клиента (прокси, таймаут)
- [ ] кеширование
- [ ] синхронизация с shikimori
- [ ] поиск и переключение по нескольким источникам в одной сессии (без перезапуска)
- [ ] конфигурация приложения
- [ ] система плагинов, кастомизация (?)
- [ ] простой http сервер-прослойка для передачи видео в плееры


