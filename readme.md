# Лабораторная работа  №1
**Студент:** Liao Xin, M4150

**Вариант:** №13	Youtube8m

**Цель работы:**

Получить навыки разработки CI/CD pipeline для ML моделей с достижением метрик моделей и качества.


**Структура каталогов:**
```
C:.
│   .dvcignore
│   .gitignore
│   dataset.dvc
│   docker-compose.yml----------------------  :конфигурация создания контейнера и образа модели;
│   Dockerfile----------------------  :конфигурация создания контейнера и образа модели;
│   requirements.txt----------------------  : используемые зависимости (библиотеки) и их версии;
│
├───.dvc
│   │   .gitignore
│   │   config
│
├───CD
│       Jenkinsfile
│
├───CI
│       Jenkinsfile
│
├───config
│       config.ini: гиперпараметры модели;
│       config.py
│
├───dataset
│       test_features.npy
│       test_ids.csv
│       train_features.npy
│       train_ids.csv
│
├───notebooks
│       youtube8m_classfication.ipynb
│
└───src
    │   data.py
    │   model.py
    │   predict.py
    │   train.py
    │
    ├───unit_tests
    │       test_preprocess.py
    │       test_training.py
    │       __init__.py

```

## Задание:

1. Создать репозитории модели на GitHub, регулярно проводить commit + push в ветку разработки, важна история коммитов;
2. Провести подготовку данных для набора данных, согласно варианту задания;
3. Разработать ML модель с ЛЮБЫМ классическим алгоритмом классификации, кластеризации, регрессии и т. д.;
4. Конвертировать модель из *.ipynb в .py скрипты;
5. Покрыть код тестами, используя любой фреймворк/библиотеку;
6. Задействовать DVC;
7. Использовать Docker для создания docker image.
8. Создать CI pipeline (Jenkins, Team City, Circle CI и др.) для сборки docker image и отправки его на DockerHub,   сборка должна автоматически стартовать по pull request в основную ветку репозитория модели;
10. Создать CD pipeline для запуска контейнера и проведения функционального тестирования по сценарию, запуск должен стартовать по требованию или расписанию или как вызов с последнего этапа CI pipeline;



## Dataset(youtube8m):

File descriptions
frame-level data

Total size of 1.53TB (Large file warning!)
Each video has
    a.  id: unique id for the video, in train set it is a YouTube video id, and in test/validation they are anonymized.
    b.  labels: list of labels of that video. c. Each frame has rgb: float array of length 1024, d. Each frame has audio: float array of length 128
A subset of the validation set videos are provided with segment-level labels. In addition to id, labels and the frame level features described above, they come with
    a. segment_start_times: list of segment start times. b. segment_end_times: list of segment end times. c. segment_labels: list of segment labels. d. segment_scores: list of binary values indicating positive or negative corresponding to the segment labels.
vocabulary.csv - the full data dictionary for label names and their descriptions

convert data to csv
```
features_path,ids_path=convert_data('train',train_tfrecord )
```

## Покрыть код тестами: 
[src\unit_tests](https://github.com/liaoxin-a/big_data/tree/main/src)
![unit_tests](https://github.com/liaoxin-a/big_data/blob/main/imgs/unit_test.PNG)

## CI/CD:
![CI](https://github.com/liaoxin-a/big_data/blob/main/imgs/CI.PNG)
![CD](https://github.com/liaoxin-a/big_data/blob/main/imgs/CD.PNG)

## docker hub:
![hub](https://github.com/liaoxin-a/big_data/blob/main/imgs/docker%20hub.PNG)

