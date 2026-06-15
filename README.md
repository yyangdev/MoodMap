# MoodMap

![Python](https://img.shields.io/badge/python-3.10%2B-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Platform](https://img.shields.io/badge/platform-linux%20%7C%20macos%20%7C%20windows-lightgrey)

<p align="center">
  Консольная утилита для подбора музыки, книг и рекомендаций на основе текстового описания состояния.
</p>

---

## Описание

MoodMap принимает текстовое описание состояния, обрабатывает его через внешние сервисы и возвращает структурированный результат: плейлист из Last.fm, книгу из Open Library и краткую рекомендацию. Приложение работает локально, не требует регистрации и не передаёт данные третьим лицам.

---

## Установка

### Зависимости

| Пакет | Версия | Назначение |
|-------|--------|------------|
| `python` | ≥ 3.10 | Среда выполнения |
| `rich` | ≥ 13.0 | Интерфейс командной строки |
| `aiohttp` | ≥ 3.9 | HTTP-клиент |
| `python-dotenv` | ≥ 1.0 | Загрузка переменных окружения |
| `loguru` | ≥ 0.7 | Логирование |

### Сборка

```bash
git clone https://github.com/yyangdev/MoodMap.git
cd moodmap
pip install -r requirements.txt
```

### Конфигурация

```bash
cp .env.example .env
```

| Переменная | Обязательно | Описание |
|------------|-------------|----------|
| `OPENROUTER_API_KEY` | Да | Ключ OpenRouter API |
| `LASTFM_API_KEY` | Да | Ключ Last.fm API |

### Запуск

```bash
python app/main.py
```

---

## Использование

### Главное меню

| Пункт | Функция |
|-------|---------|
| `1` | Подбор плейлиста |
| `2` | Поиск книги |
| `3` | Получение совета |
| `4` | Полная рекомендация |
| `5` | История запросов |
| `6` | Статистика |
| `0` | Выход |

### Пример

```
> 4
Опишите состояние: устал после работы, хочется покоя

Состояние: 3/10

Плейлист:
  1. Bon Iver — Holocene
  2. Sufjan Stevens — Mystery of Love
  3. Cigarettes After Sex — Apocalypse

Книга: «Искусство покоя» — Тит Нат Хан

Совет: 15 минут тишины с чаем
```

---

## API

| Сервис | Endpoint | Аутентификация |
|--------|----------|----------------|
| OpenRouter | `POST /api/v1/chat/completions` | Bearer Token |
| Last.fm | `GET /2.0/` | API Key |
| Open Library | `GET /search.json` | Нет |

Подробнее: [app/API/api_docs.md](app/API/api_docs.md)

---

## Структура проекта

```
app/
├── api/              # Клиенты внешних сервисов
│   ├── router.py     #   OpenRouter
│   ├── music.py      #   Last.fm
│   ├── book.py       #   Open Library
│   └── storage.py    #   Локальное хранилище
├── core/             # Модели, конфигурация, исключения
│   ├── config.py     #   Загрузка .env
│   ├── models.py     #   Dataclass-модели
│   ├── exceptions.py #   Кастомные ошибки
│   └── logger.py     #   Логирование
├── service/          # Бизнес-логика
│   ├── mood.py       #   Определение настроения
│   ├── recommendation.py # Сборка рекомендаций
│   └── stats.py      #   Статистика
├── ui/               # Консольный интерфейс
│   ├── console.py    #   Настройка Rich
│   ├── menu.py       #   Главное меню
│   ├── prompts.py    #   Пользовательский ввод
│   └── views.py      #   Вывод результатов
└── main.py           # Точка входа
```

| Модуль | Документация |
|--------|-------------|
| `core` | [core_docs.md](app/core/core_docs.md) |
| `service` | [service_docs.md](app/service/service_docs.md) |
| `ui` | [ui_docs.md](app/ui/ui_docs.md) |
| `api` | [api_docs.md](app/API/api_docs.md) |

---

## Лицензия

MIT. См. [LICENSE](LICENSE).
```
git commit -m "Fix README formatting"
git push
```
