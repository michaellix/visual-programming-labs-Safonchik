# Лабораторная работа №3. Bubble

**Тема:** План тренировок


## Часть 1. Промпт и генерация каркаса

### Промпт
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
![02-buildguide-search-1](../screenshots/search-1-workout-tracker-app.png)
![02-buildguide-search-2](../screenshots/search-2-fitness-tracker-app.png)
![02-buildguide-search-3](../screenshots/search-3-training-plan-app.png)
![02-buildguide-search-4](../screenshots/search-4-workout-schedule-app.png)

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

![02-buildguide-before](../screenshots/02-buildguide-before.png)

**После:**  между формой и списком добавлен Progress Bar,
показывающий процент выполненных тренировок.

Настройки Progress Bar:
- Value = `Search for Workouts:filtered (Completed = yes):count`
- Max value = `Search for Workouts:count`
- Bar color = `#2E7D32`
- Background color = `#EEEEEE`

Под Progress Bar добавлена динамическая подпись:
«Прогресс: выполнено X из Y тренировок».

![02-buildguide-after](../screenshots/02-buildguide-after.png)

## Часть 3. Ручная доработка UI
### 3.1. Изменение заголовка
В шапке и подвале текст заменён на «ТВП: Сафончик Михаил».

![03-title](../screenshots/03-title.png)

### 3.2. Global variable для цвета
Создана переменная primary-color
Применена к кнопке «Добавить тренировку» (Background color).

![03-global-variable](../screenshots/03-global-variable.png)
![03-global-variable](../screenshots/03-global-variable-result.png)

### 3.3. Новый стиль
Создан стиль Primary Button для кнопок.
Использует primary-color как фон, белый текст, скруглённые углы.
Применён к кнопке «Добавить тренировку».
![04-style](../screenshots/04-style-settings.png)
![04-style](../screenshots/04-style.png)
![04-style](../screenshots/04-style-result.png)

### 3.4. Готовый компонент
Из библиотеки Components добавлен footer и настроен под тематику сайта 
![05-component](../screenshots/05-component.png)

## Часть 4. Data и Workflows

**AI-промпт для сущности:**
Придумай название и поля для новой сущности в приложении
«План тренировок». Нужно минимум 3 поля разных типов: текст,
дата, да/нет. Сущность должна описывать одну тренировку и её детали.

**Сущности**
![06-data-type](../screenshots/06-data-type.png)
![06-data-type-2](../screenshots/06-data-type-2.png)

Также добавлены 3 записи вручную через App Data:

![07-data-records](../screenshots/07-data-records.png)

### 4.2. Workflows: CRUD

**Проверено в Preview:** все  операции CRUD (Create, Read, Update,
Delete) работают корректно.
![08-workflow-create](../screenshots/08-workflow-create.png)

**Все workflow:**

Добавить тренировку:
![09-workflow-create](../screenshots/08-workflow-create.png)

Внести изменения:
![09-workflow-edit](../screenshots/09-workflow-change.png)

Изменить тренировку(окончательно):
![09-workflow-save](../screenshots/09-workflow-edit.png)

Сохранить:
![09-workflow-change](../screenshots/09-workflow-save.png)

Отменить:
![09-workflow-cancel](../screenshots/09-workflow-cancel.png)

Удалить:
![09-workflow-delete](../screenshots/09-workflow-delete.png)

Навигация на страницу с тренировками:
![navigation.png](../screenshots/navigation.png)

Навигация на главную:
![navigation-2.png](../screenshots/navigation-2.png)


Ссылка:
https://michaelsafonchik.bubbleapps.io/version-test?debug_mode=true


Выводы:

В ходе работы я освоил Bubble на базовом уровне:

- Сгенерировал каркас приложения через AI-агента Bubble.
- Изучил Build Guides, выбрал фичи уровня MODERATE и применил идею Progress tracking.
- Освоил ручную доработку UI
- Создал сущность Тренировка с полями разных типов.
- Реализовал полный CRUD через workflows: Create, Read, Update, Delete.
- Настроил навигацию между страницами.
- Понял, как AI ускоряет разработку
