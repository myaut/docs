## Строковые {#string}

| Тип    | Пояснение      | Используется в<br/>запросах и<br/>вычислениях<br/>YQL | Используется в<br/>качестве типа<br/>данных столбца | Используется в<br/>первичных<br/>ключах | Поддерживает<br/>возможность<br/>сравнения |
| ----- | ----- | ----- | ----- | ----- | ----- |
| **String** | Может содержать произвольные бинарные данные | Да | Да | Да | Да |
| **Utf8** | Содержит текст в&nbsp;кодировке UTF-8 | Да | Да | Да | Да |
| **Json** | Содержит JSON | Да | Да | Нет | Нет |
| **Yson** | Содержит YSON | Да | Да | Нет | Нет |
| **Uuid** | Содержит UUID | Да | Нет | Нет | Да |

Максимальный размер значения в ячейке с любым строковым типом данных — около 4 МБ.
