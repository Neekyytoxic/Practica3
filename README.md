# Practica3
## Задание 1: Список всех Docker-контейнеров с датой

```
#!/bin/bash

DATE=$(date +"%Y-%m-%d_%H-%M-%S")
FILE="containers-$DATE.txt"

echo "Дата проверки: $(date)" > $FILE
docker ps >> $FILE

echo "Результат сохранён в $FILE"

```

<img width="917" height="245" alt="image" src="https://github.com/user-attachments/assets/13b6fe54-8e3f-411c-b523-d6581c3171a8" />

## Задание 2: Проверка доступности веб-сервиса через curl

```
#!/bin/bash

URL="http://localhost:8080"
DATE=$(date +"%Y-%m-%d")
LOG="errors-$DATE.log"

STATUS=$(curl -o /dev/null -s -w "%{http_code}" $URL)

if [ "$STATUS" = "200" ]; then
    echo "$URL - OK - $(date)"
else
    echo "$URL - FAIL - $(date)" | tee -a $LOG
fi

```

<img width="668" height="157" alt="image" src="https://github.com/user-attachments/assets/a49c0b13-ae17-451e-84e9-c723fe386768" />

## Задание 3: Сколько места занимает каждый Docker-образ

```
#!/bin/bash

DATE=$(date +"%Y-%m-%d")
FILE="docker-images-sizes-$DATE.txt"

echo "Дата: $(date)" > $FILE
docker images --format "table {{.Repository}}\t{{.Tag}}\t{{.Size}}" >> $FILE

echo "Самый большой образ:" >> $FILE
docker images --format "{{.Repository}} {{.Size}}" | sort -hr -k2 | head -1 >> $FILE

```

<img width="693" height="333" alt="image" src="https://github.com/user-attachments/assets/022f8871-fcd9-4069-9059-3d0179a5f8f3" />

## Задание 4: Синхронизация одного Git-репозитория

<img width="517" height="67" alt="image" src="https://github.com/user-attachments/assets/11cd2bc1-bf03-45f3-be0c-53247480ef98" />

<img width="1123" height="362" alt="image" src="https://github.com/user-attachments/assets/e2c4ec36-a23e-471a-b3bf-9e1d49e5b817" />

## Задание 5: Проверка статуса Docker-контейнера

<img width="970" height="219" alt="image" src="https://github.com/user-attachments/assets/2d90f155-7025-4c83-b316-b25eaf1f70ca" />

<img width="900" height="297" alt="image" src="https://github.com/user-attachments/assets/53b7da8b-777c-4134-8ef8-17dd55fc289a" />


## Задание 6-7: Скачивание файла с проверкой через curl и удаление старых Docker-контейнеров

<img width="850" height="300" alt="image" src="https://github.com/user-attachments/assets/d098c42f-1c03-4e30-98ed-5faa0fe44921" />
