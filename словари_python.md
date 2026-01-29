# Словари в Python


Словарь (dictionary) в языке Python хранит коллекцию элементов, где каждый элемент имеет уникальный ключ и ассоциированное с ним некоторое значение.

## Создание словаря

### Базовый синтаксис
```python
dictionary = {ключ1: значение1, ключ2: значение2, ...}
```

**Примеры:**
```python
users = {1: "Tom", 2: "Bob", 3: "Bill"}
emails = {"tom@gmail.com": "Tom", "bob@gmail.com": "Bob"}
objects = {1: "Tom", "2": True, 3: 100.6}  # Разные типы ключей и значений
```

### Пустой словарь
```python
objects = {}
# или
objects = dict()
```

### Преобразование из списка/кортежа
```python
users_list = [
    ["+111123455", "Tom"],
    ["+384767557", "Bob"]
]
users_dict = dict(users_list)
# {"+111123455": "Tom", "+384767557": "Bob"}

users_tuple = (
    ("+111123455", "Tom"),
    ("+384767557", "Bob")
)
users_dict = dict(users_tuple)
```

## Работа с элементами

### Получение значения
```python
users = {"+11111111": "Tom", "+33333333": "Bob"}

# Прямое обращение (вызывает KeyError при отсутствии ключа)
user = users["+11111111"]  # "Tom"

# Метод get() (безопасный способ)
user1 = users.get("+55555555")           # None, если ключа нет
user2 = users.get("+33333333", "Unknown") # "Bob"
user3 = users.get("+44444444", "Unknown") # "Unknown"
```

### Изменение и добавление
```python
users["+33333333"] = "Bob Smith"  # Изменение существующего
users["+4444444"] = "Sam"         # Добавление нового
```

### Проверка наличия ключа
```python
key = "+4444444"
if key in users:
    user = users[key]
else:
    print("Элемент не найден")
```

## Удаление элементов

### Оператор del
```python
del users["+55555555"]  # KeyError, если ключа нет

# Безопасное удаление
key = "+55555555"
if key in users:
    del users[key]
```

### Метод pop()
```python
user = users.pop("+55555555")            # Возвращает значение
user = users.pop("+4444444", "Unknown")  # С значением по умолчанию
```

### Очистка словаря
```python
users.clear()  # Полная очистка
```

## Копирование и объединение

### Копирование
```python
students = users.copy()
```

### Объединение
```python
users = {"+1111111": "Tom", "+3333333": "Bob"}
users2 = {"+2222222": "Sam", "+6666666": "Kate"}

users.update(users2)  # users изменяется, users2 - нет

# Без изменения оригиналов
users3 = users.copy()
users3.update(users2)
```

## Перебор словаря

### Перебор ключей
```python
for key in users:
    print(f"Phone: {key} User: {users[key]}")

# или
for key in users.keys():
    print(key)
```

### Перебор пар ключ-значение
```python
for key, value in users.items():
    print(f"Phone: {key} User: {value}")
```

### Перебор значений
```python
for value in users.values():
    print(value)
```

## Комплексные словари

### Вложенные словари
```python
users = {
    "Tom": {
        "phone": "+971478745",
        "email": "tom12@gmail.com"
    },
    "Bob": {
        "phone": "+876390444",
        "email": "bob@gmail.com",
        "skype": "bob123"
    }
}
```

### Доступ к вложенным элементам
```python
# Получение значения
old_email = users["Tom"]["email"]

# Изменение
users["Tom"]["email"] = "supertom@gmail.com"

# Безопасный доступ
tom_skype = users["Tom"].get("skype", "Undefined")
```

---

## Сводная таблица: Создание и обработка словарей

| Операция | Синтаксис | Пример | Описание |
|----------|-----------|--------|----------|
| **Создание** | `{}` | `d = {}` | Пустой словарь |
| | `{k:v, ...}` | `d = {"a": 1, "b": 2}` | Создание с элементами |
| | `dict()` | `d = dict()` | Конструктор пустого словаря |
| | `dict(iterable)` | `d = dict([("a",1), ("b",2)])` | Из списка кортежей |
| **Доступ** | `d[key]` | `value = d["a"]` | Получение значения (KeyError если нет) |
| | `d.get(key)` | `value = d.get("a")` | Безопасное получение (None если нет) |
| | `d.get(key, default)` | `value = d.get("c", 0)` | Со значением по умолчанию |
| **Проверка** | `key in d` | `if "a" in d:` | Проверка наличия ключа |
| | `key not in d` | `if "z" not in d:` | Проверка отсутствия ключа |
| **Добавление/Изменение** | `d[key] = value` | `d["c"] = 3` | Добавление или изменение |
| | `d.update(other)` | `d.update({"d":4})` | Объединение словарей |
| **Удаление** | `del d[key]` | `del d["a"]` | Удаление по ключу |
| | `d.pop(key)` | `value = d.pop("b")` | Удаление с возвратом значения |
| | `d.pop(key, default)` | `val = d.pop("z",0)` | Удаление со значением по умолчанию |
| | `d.popitem()` | `k,v = d.popitem()` | Удаление последней пары (Python 3.7+) |
| | `d.clear()` | `d.clear()` | Полная очистка |
| **Копирование** | `d.copy()` | `d2 = d.copy()` | Поверхностное копирование |
| **Перебор** | `d.keys()` | `for k in d.keys():` | Перебор ключей |
| | `d.values()` | `for v in d.values():` | Перебор значений |
| | `d.items()` | `for k,v in d.items():` | Перебор пар ключ-значение |
| **Информация** | `len(d)` | `size = len(d)` | Количество элементов |
