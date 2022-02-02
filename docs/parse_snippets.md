# Функция *parseSnippets*

## Назначение функции

Функция для загрузки шаблонов кода (сниппетов) в формате 1С:Предприятия

## Параметры функции

* **stData** - *string*, текстовое содержимое файла шаблона .st

## Пример вызова

```javascript
parseSnippets('{0,{"Пока",0,0,"Пока","Пока <?""Условие""> Цикл......');
```

## Особенности реализации

1. В списке подсказок появляются только те шаблоны кода, у которых в 1С заполнено поле `Автоматически заменять строку`.
2. В стандартных шаблонах 1С для списка выбора есть возможность указывать представление значение и само вставляемое значение, например, так:

```bsl
<?"", ВыборВарианта, "Основная таблица", "<?>", "СрезПервых", ".СрезПервых(<?>)", "СрезПоследних", ".СрезПоследних(<?>)">
```

При выборе значения `Основная таблица` в код фактически не вставляется ничего, а просто происходит перемещение курсора в текущую позицию. К сожалению, редактор не позволяет реализовать такую схему, поэтому указанный выше шаблон преобразуется в выбор из двух значений, а именно `СрезПервых` и `СрезПоследних`.

3. Шаблон `ДатаВремя` всегда преобразуется в текущую дату в формате `dd.MM.yyyy HH:mm:ss`
4. Шаблоны, предназначенные для выбора объекта метаданных, такие как `Справочник`, `Документ`, `РегистрСведений` и подобные преобразуются в список выбора соответствующих объектов. Если метаданные ранее не были загружены через функцию [`updateMetadata`](update_metadata.md), тогда при активизации сниппета в списке подсказок происходит генерация события [`EVENT_GET_METADATA`](get_metadata_event.md) после обработки которого в 1С следует дополнительно вызвать метод [`updateSnippetByGUID`](update_snippet_guid.md)
5. Перечисленные ниже шаблоны никак не обрабатываются, а просто вставляются в код с аналогичным именем переменной:

* ВыборТипа
* ЖурналДокументов
* ЗначениеПеречисления
* ИмяПользователя
* ПолноеИмяПользователя
* ИмяПользователяХранилищаКонфигурации
* КонструкторОписанияТипов
* КритерийОтбора
* ОбъектМетаданных
* Перерасчет
* ПланВидовРасчетаПредопределенныеДанные
* ПланВидовХарактеристикПредопределенныеДанные
* ПланСчетовПредопределенныеДанные
* Последовательность
* СправочникПредопределенныеДанные
* ТекстЗапроса
* ФорматнаяСтрока