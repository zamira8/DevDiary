markdown
# DevDiary
**TrackAnalyzer** - это **легкое** консольное приложение для анализа музыкальных треков. Поддерживает **Markdown**, **теги** и **поиск** по записям.

##Оглавление
-[Возможности](#Возможности)
-[Установка](#Установка)
-[Использование](#Использование)
-[Параметры](#Параметры)
-[Возвращение](#Возвращение)
-[Roadmap](#Roadmap)

![Status](https://avatars.mds.yandex.net/i?id=7b83a93f7adece6907a558901a881d14_l-4494838-images-thumbs&n=13)

##Возможности
-Подсчет общей и средней длительности треков
-Топ исполнителей по прослушиваниям
-Распределение по жанрам, годам и странам
-Среднее соотношение лайков к прослушиваниям
-Определение самого популярного жанра
-Фильтрация

##Установка
1. Установите Python 3.10+
2. Клонируйте репозиторий
3. Дополнительные зависимости не требуются

'''bash
git clone https://github.com/user/devdiary.git
cd devdiary
pip instal -r requirements.txt
'''

>**Важно:** для корректной работы требуется 'sqlite3' версия 3.35+.

##Использование

from analyzer import analyze_tracks
tracks = [
  {
    "title": "hotel",
    "artist": "Montell Fish",
    "album": "Her Love Still Haunts Me Like a Ghost",
    "genry": "pop",
    "duration_sec": 197,
    "year": 202",
    "plays": 800000,          
    "likes": 70000,
    "is_explicit": False,
    "country": "US",
    },


result = analyze_tracks(
    tracks,
    genre_filter="R&B",
    year_from=2020,
    year_to=2025,
    min_duration=120,
    top_n=5,
    include_explicit=False,
)

##Параметры

Параметр |	Тип	| Описание
tracks |	list[dict]	| Список треков
genre_filter |	str | None | Фильтр по жанру (None — все)
year_from |	int | None |	Минимальный год
year_to |	int | None	|Максимальный год
min_duration	| int | None |	Минимальная длительность (сек)
top_n |	int	| Размер топ-выборок (по умолчанию 5)

##Возвращает

Ключ | Описание
total_duration_sec | Общая длительность
average_duration_sec | Средняя длительность
top_tracks | Топ треков по прослушиваниям
top_artists | Топ исполнителей
by_genre | Количество треков по жанрам
by_year | Количество треков по годам
by_country | Количество треков по странам
avg_likes_ratio | Среднее соотношение лайков к прослушиваниям
most_popular_genre | Самый популярный жанр

##Roadmap

+ Фильтрация по жанру, годам, длительности и explicit
+ Топ-N треков и исполнителей
+ Распределения по жанрам, годам, странам
- Кэширование тяжёлых агрегаций
- Экспорт отчёта в CSV / JSON
- Поддержка стриминговых API (Spotify, Яндекс музыка)

