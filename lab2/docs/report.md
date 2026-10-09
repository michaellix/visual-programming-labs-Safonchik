# Отчёт по лабораторной работе №2 (Node-RED)

## Основное

Собрал 12 потоков в Node-RED, каждый на отдельной вкладке. Все экспортировал в JSON и сделал скриншоты.

## AI-промпты:

Function node:
Напиши JavaScript-код для ноды Function в Node-RED:
использовать let/const, if/else, for, массив, объект.
На вход — msg.payload (число 1-10). Вернуть объект со статусом и суммой.


Template node:
Напиши Mustache-шаблон для ноды Template в Node-RED.
На вход — объект с полями name, group, timestamp. Формирует JSON.

## Освоенные ноды

inject, debug, function, switch, change, template, http in, http response, http request, mqtt in, mqtt out, file in, file out, telegram receiver, telegram sender, ui_gauge, ui_chart, flow context.

## Установка и версии

- Способ: Docker
- Образ: nodered/node-red:latest
- Node-RED: v5.0.8
- Node.js: v24.21.0
- Порт: 1880
- Volume: ~/Documents/GitHub/visual-programming-labs-Safonchik/lab2/data:/data

## Скриншоты

### Версии
![versions](../screenshots/versions.png)

### 01-inject-debug
![inject-debug](../screenshots/01-inject-debug.png)

### 02-function
![function](../screenshots/02-function.png)

### 03-switch
![switch](../screenshots/03-switch.png)

### 04-change
![change](../screenshots/04-change.png)

### 05-template
![template](../screenshots/05-template.png)

### 06-http-request
![http-request](../screenshots/06-http-request.png)

### 07-mqtt
![mqtt](../screenshots/07-mqtt.png)

### 08a-endpoints-text
![endpoints-text](../screenshots/08a-endpoints-text.png)

### 08b-endpoints-info
![endpoints-info](../screenshots/08b-endpoints-info.png)

### 08c-endpoints-items-success
![items-success](../screenshots/08c-endpoints-items-success.png)

### 08d-endpoints-items-error
![items-error](../screenshots/08d-endpoints-items-error.png)

### 08e-endpoints-items-404
![items-404](../screenshots/08e-endpoints-items-404.png)

### 09-dashboard
![dashboard](../screenshots/09-dashboard.png)

### 10-telegram
![telegram](../screenshots/10-telegram.png)

### 11-files
![files](../screenshots/11-files.png)

### 12-context
![context](../screenshots/12-context.png)

## Выводы

Разобрался с Node-RED. Понял, что потоки - это ноды, соединённые стрелками, данные передаются в msg. Node-RED - хороший инструмент для быстрого прототипирования короче
