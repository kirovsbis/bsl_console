# Функция *updateVariableDescription*

## Назначение функции

Используется для обновления значения переменной в табло. Функцию следует использовать для ответа на событие [`EVENT_GET_VARIABLE_DATA`](get_var_data_event.md)

## Параметры функции

* **variableId** - *string*, уникальный ключ (идентификатор) переменной
* **variableJSON** - *string*, массив с данными переменной виде JSON-объекта, со следующими полями:
  * [label] - *строка*, имя переменной
  * [value] - *строка*, значение переменной
  * [type] - *строка*, тип переменной
  * [path] - *строка*, путь для получения значения переменной.
  * [class] - *строка*, **final** для переменных, дальнейшая расшифровка которых не требуется. Например, для переменных с примитивны типами
  * [icon] - *строка*, картинка для переменной. Может принимать значения с именами файлов из каталога `./tree/icons`
  * [children] - *строка*, данные переменной (реквизиты, табличные части и т.п.), содержащие поля, указанные выше
	
## Примеры вызова функции

```javascript
updateVariableDescription('var_b13b613706d945b6a7cb73faaeceff8d', `{
  "var_b13b613706d945b6a7cb73faaeceff8d": {
    "label": "ВидНоменклатуры",
    "value": "<a href='e1cib/data/Справочник.ВидыНоменклатуры?ref=80e20050569f16cd11e6d8d63deb713b'>Услуги</a>",
    "type": "Вид номенклатуры",
    "path": "var_b13b613706d945b6a7cb73faaeceff8d",
    "class": "",
    "icon": "catalog.png",
    "children": {
      "var_e00ab5471573473e81a0c02299da5880": {
        "label": "УникальныйИдентификатор",
        "value": "3deb713b-d8d6-11e6-80e2-0050569f16cd",
        "type": "Уникальный идентификатор",
        "path": "var_b13b613706d945b6a7cb73faaeceff8d.УникальныйИдентификатор",
        "class": "final",
        "icon": "uuid.png"
      },
      "var_b8d81a566dcc4441b3bd754fd1b954cf": {
        "label": "ПометкаУдаления",
        "value": "Нет",
        "type": "Булево",
        "path": "var_b13b613706d945b6a7cb73faaeceff8d.ПометкаУдаления",
        "class": "final",
        "icon": "boolean.png"
      },
      "var_3a30ab9aabaa432a80372f590ca10c97": {
        "label": "Наименование",
        "value": "Услуги",
        "type": "Строка",
        "path": "var_b13b613706d945b6a7cb73faaeceff8d.Наименование",
        "class": "final",
        "icon": "string.png"
      },
      "var_5aa921edaf774a8bb3e82f604a901cbd": {
        "label": "ГруппаАналитическогоУчета",
        "value": "",
        "type": "Группа аналитического учета номенклатуры",
        "path": "var_b13b613706d945b6a7cb73faaeceff8d.ГруппаАналитическогоУчета",
        "class": "",
        "icon": "catalog.png"
      }
    }
  }
}`);
```