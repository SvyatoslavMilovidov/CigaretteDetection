# CigaretteDetection

## Краткое описание

- Необходимо создавать bbox на фотографиях, где есть сигарета. Сигареты могут быть как обычные, так и электронные.
- Стек: `ultralytics`, `matplotlib`, `numpy`, `opencv-python`, `torch-vision`

## Создание датасета

Формирование тренировоного датасета производилось руками (хотя можно было соорудить парсер).

- Количество фотографий в тренировочном датасете - 100.
- Тестовый датасет содержит 180 фотографий.

Тестовый датасет был получен от компании, поэтому вышло, что количество фотографий в нем превосходит тренировочный.

<img src="readme_imgs\sample_raw_data.jpg" swidth="200" height="300">

### Разметка данных

Для разметки данных использовалась `Roboflow`. Данные размечены под формат YOLO (v8).

Ну, здравствуй...

<img src="readme_imgs\sample_ready_data.png" swidth="200" height="300">


### Обучение модели

В качетсве модели была выбрана `YOLOv8n`. [0ссновные характеристики моделей](https://docs.ultralytics.com/models/yolov8/#supported-modes).

Для оценки результата рассмотрим PR-кривую (класс только один, пожтому график подойдёт)

<img src="readme_imgs\PR_curve.png" swidth="200" height="300">

Модель может выделять искомые объекты, но с небольшой увернностью. Что можно сделать, чтобы увеличит качество:

- увеличить объем тренировочных данных
- провести более тонкую настройку параметров модели (например, добавить sheduler)
- аугмментировать данные
- использовать предобученную модель