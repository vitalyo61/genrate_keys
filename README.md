# REST-сервис #

Генерация и выдача уникальных ключей и их последующее погашение. Пример такого сервиса: подтверждение платежей банком по SMS.

Для работы сервиса необходим сервер **MongoDB**.
Для запуска необходим в каталоге запуска файл конфигурации `genkeys.conf`.

## genkeys.conf ##

```
[server]
        # Адрес сервера
        address = "localhost:8080"
        # Время ожидания ответа от сервера в секундах
        timeout = 10

[data_base]
        # Адрес сервера MongoDB
        url = "localhost:27017"
```

## API ##

| название                      | адрес              | параметр | ответ                                               | код статуса   |
|-------------------------------|--------------------|----------|-----------------------------------------------------|---------------|
| Выдача уникальных ключей      | /generate          |          | ключ или описание ошибки                            | 200, 503, 500 |
| Погашение ключа               | /extinguish/{code} | ключ     | отсутствует или описание ошибки                     | 200, 500      |
| Проверка ключа                | /info/{code}       | ключ     | `не выдан`, `выдан`, `погашен`, или описание ошибки | 200, 500      |
| количество не выданных ключей | /count             |          | число или описание ошибки                           | 200           |

