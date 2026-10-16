# Лабораторная работа №3. Bubble

**Тема:** План тренировок
**Студент:** Сафончик
**Платформа:** Bubble (бесплатный план)

## Часть 1. Промпт и генерация каркаса

### Промпт (дословно)
Создай приложение на тему «План тренировок»
Пусть этот сайт будет публичный
Страницу обязательно создай по структуре header + body + footer
Обязательно укажи в заготовке следующую строку: «ТВП: Сафончик»
Добавь несколько интерактивных элементов (реализующих CRUD): список тренировок,
форму для добавления новой тренировки с полями «Название», «Дата», «Тип тренировки»,
кнопки редактирования и удаления каждой тренировки


## Часть 2. Исследование идеи (Build Guides)

Я ввёл в строку поиска Build Guides 4 запроса:
1. workout tracker app
2. fitness tracker app
3. training plann app
4. workout schedule app

AI Bubble сгенерировал для каждого запроса персонализированный список
рекомендованных фич (Build Guides) с пометками сложности MODERATE / CHALLENGING.

### Скриншоты генераций:
![02-buildguide-search-1](screenshots/search-1-workout-tracker-app.png)
![02-buildguide-search-2](screenshots/search-2-fitness-tracker-app.png)
![02-buildguide-search-3](screenshots/search-3-training-plan-app.png)
![02-buildguide-search-4](screenshots/search-4-workout-schedule-app.png)

### Выбранные Build Guides

**1. Workout logging (MODERATE)**
Из гайда «Start building your Workout Tracker» (запрос "training plan app").
Описание: ведение журнала тренировок с упражнениями, подходами, повторениями и длительностью.
Что взял: структуру «список тренировок + форма добавления», которая легла в основу
сущности "Workout" и CRUD-workflow.

**2. Progress tracking (MODERATE)**
Из гайда «Start building your Workout Tracker».
Описание: визуализация прогресса тренировок во времени.
Что взял: Progress Bar, показывающий процент выполненных тренировок.

### Что просмотрел
- Как AI Bubble формирует персонализированные рекомендации по фичам.
- Как отличать MODERATE от CHALLENGING и выбирать посильные для бесплатного плана.
- Как связать список записей с формой добавления через Workflow.

### Что показалось полезным
- Разметка сложности (MODERATE/CHALLENGING) помогает не брать слишком сложные фичи.
- Progress tracking можно реализовать не через громоздкий dashboard, а через простой Progress Bar.
- Workout logging — это фактически CRUD, что можно сказать закрывает требования Части 4.

### Что взял в своё приложение
- CRUD-структуру для сущности Workout (из Workout logging).
- Progress Bar для отображения прогресса (из Progress tracking).

### Применение идеи: «До» и «После»

**Идея:** Progress tracking через Progress Bar.
Взято из Build Guide «Start building your Workout Tracker»
(фича Progress tracking, MODERATE).

**До:** страница содержала форму «Новая тренировка» и список
«Ваши тренировки» без индикатора прогресса.
Пользователь не видел, сколько тренировок уже выполнено.

![02-buildguide-before](screenshots/02-buildguide-before.png)

**После:** в шапку добавлено имя «ТВП: Сафончик»,
а между формой и списком добавлен Progress Bar,
показывающий процент выполненных тренировок.

Настройки Progress Bar:
- Value = `Search for Workouts:filtered (Completed = yes):count`
- Max value = `Search for Workouts:count`
- Bar color = `#2E7D32`
- Background color = `#EEEEEE`

Под Progress Bar добавлена динамическая подпись:
«Прогресс: выполнено X из Y тренировок».

![02-buildguide-after](screenshots/02-buildguide-after.png)

## Часть 3. Ручная доработка UI
...

## Часть 4. Data и Workflows
...

