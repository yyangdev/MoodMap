# MoodMap

![Python](https://img.shields.io/badge/python-3.10%2B-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20Linux%20%7C%20macOS-lightgrey)

Консольная утилита для подбора музыки, книг и рекомендаций. Пишете пару слов о состоянии — получаете плейлист, книгу и совет.

---

## Установка

```bash
git clone https://github.com/yyangdev/MoodMap.git
cd MoodMap
pip install -r requirements.txt
```

| Пакет | Версия |
|-------|--------|
| python | ≥ 3.10 |
| rich | ≥ 13.0 |
| aiohttp | ≥ 3.9 |
| python-dotenv | ≥ 1.0 |
| loguru | ≥ 0.7 |

### Ключи

| Сервис | Где получить |
|--------|-------------|
| OpenRouter | [openrouter.ai/keys](https://openrouter.ai/keys) |
| Last.fm | [last.fm/api](https://www.last.fm/api/account/create) |

Создать `.env`:

```
OPENROUTER_API_KEY=sk-or-...
LASTFM_API_KEY=...
```

### Запуск

```bash
python app/main.py
```

Или скачать `MoodMap.exe` из [релизов](https://github.com/yyangdev/MoodMap/releases).

---

## Меню

| Клавиша | Действие |
|---------|----------|
| `1` | Плейлист |
| `2` | Книга |
| `3` | Совет |
| `4` | Всё сразу |
| `5` | История |
| `6` | Статистика |
| `0` | Выход |

---

## API

| Сервис | Endpoint | Ключ |
|--------|----------|------|
| OpenRouter | `POST /api/v1/chat/completions` | Bearer |
| Last.fm | `GET /2.0/` | api_key |
| Open Library | `GET /search.json` | нет |

---

## Структура

```
app/
├── api/          # Клиенты API
│   ├── router.py # OpenRouter
│   ├── music.py  # Last.fm
│   ├── book.py   # Open Library
│   └── storage.py
├── core/         # Конфиг, модели, ошибки
│   ├── config.py
│   ├── exceptions.py
│   └── logger.py
├── service/      # Бизнес-логика
│   ├── mood.py
│   ├── recommendation.py
│   └── stats.py
├── ui/           # Интерфейс
│   ├── console.py
│   ├── menu.py
│   ├── prompts.py
│   └── views.py
└── main.py
```

| Модуль | Документация |
|--------|-------------|
| core | [core_docs.md](app/core/core_docs.md) |
| service | [service_docs.md](app/service/service_docs.md) |
| ui | [ui_docs.md](app/ui/ui_docs.md) |
| api | [api_docs.md](app/API/api_docs.md) |

---

## Лицензия

MIT. См. [LICENSE](LICENSE).
```
