# 🚀 Шпаргалка по спискам в Python

## 📋 Создание списков

```python
# Пустой список
empty_list = []
empty_list = list()

# Список с элементами
numbers = [1, 2, 3, 4, 5]
fruits = ['apple', 'banana', 'orange']
mixed = [1, 'hello', 3.14, True]

# Преобразование в список
text = "hello"
chars = list(text)  # ['h', 'e', 'l', 'l', 'o']

# Генерация списков
from_range = list(range(5))      # [0, 1, 2, 3, 4]
from_string = "a b c".split()    # ['a', 'b', 'c']
```

## 🔍 Доступ к элементам

```python
items = ['a', 'b', 'c', 'd', 'e']

# По индексу (с начала)
first = items[0]    # 'a'
second = items[1]   # 'b'

# По индексу (с конца)
last = items[-1]    # 'e'
pre_last = items[-2] # 'd'

# Срезы (slice)
slice1 = items[1:4]     # ['b', 'c', 'd'] 
slice2 = items[:3]      # ['a', 'b', 'c']
slice3 = items[2:]      # ['c', 'd', 'e']
slice4 = items[::2]     # ['a', 'c', 'e'] (каждый второй)
slice5 = items[::-1]    # ['e', 'd', 'c', 'b', 'a'] (реверс)
```

## ✏️ Изменение списков

```python
# Добавление элементов
nums = [1, 2, 3]
nums.append(4)          # [1, 2, 3, 4]
nums.insert(1, 99)      # [1, 99, 2, 3, 4] (в позицию 1)
nums.extend([5, 6])     # [1, 99, 2, 3, 4, 5, 6]

# Удаление элементов
nums.remove(99)         # [1, 2, 3, 4, 5, 6] (по значению)
popped = nums.pop()     # 6, список: [1, 2, 3, 4, 5]
popped2 = nums.pop(0)   # 1, список: [2, 3, 4, 5]
del nums[1]             # [2, 4, 5] (удаляет элемент на позиции 1)

# Изменение элементов
nums[0] = 100           # [100, 4, 5]
nums[1:3] = [7, 8, 9]   # [100, 7, 8, 9] (замена среза)
```

## 📊 Основные методы

```python
data = [1, 2, 3, 2, 4]

# Информация о списке
length = len(data)          # 5
count_2 = data.count(2)     # 2 (сколько раз встречается 2)
index_3 = data.index(3)     # 2 (индекс первого вхождения 3)

# Сортировка и реверс
data.sort()                 # [1, 2, 2, 3, 4] (сортировка на месте)
data.reverse()              # [4, 3, 2, 2, 1] (реверс на месте)

# Копирование
copy1 = data.copy()         # Поверхностная копия
copy2 = data[:]             # Альтернативный способ копирования
```

## 🔄 Работа с несколькими списками

```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]

# Конкатенация
combined = list1 + list2    # [1, 2, 3, 4, 5, 6]

# Повторение
repeated = list1 * 2        # [1, 2, 3, 1, 2, 3]

# Проверка вхождения
exists = 2 in list1         # True
not_exists = 7 in list1     # False
```

## 🎯 Практические примеры

### Обработка данных
```python
# Сумма, максимум, минимум
grades = [85, 92, 78, 90, 88]
average = sum(grades) / len(grades)    # 86.6
best = max(grades)                     # 92
worst = min(grades)                    # 78

# Фильтрация
passed = [grade for grade in grades if grade >= 80]  # [85, 92, 90, 88]
```

### Работа со строками
```python
# Разделение и объединение
text = "apple,banana,orange"
fruits = text.split(',')               # ['apple', 'banana', 'orange']
new_text = ' - '.join(fruits)          # 'apple - banana - orange'
```

### Стек (LIFO)
```python
stack = []
stack.append('task1')  # Добавить в конец
stack.append('task2')
current = stack.pop()  # Взять последний -> 'task2'
```

### Очередь (FIFO)
```python
from collections import deque
queue = deque(['user1', 'user2'])
queue.append('user3')      # В конец
current = queue.popleft()  # Из начала -> 'user1'
```

## 💡 Полезные приемы

### Генераторы списков
```python
# Создание списка квадратов
squares = [x**2 for x in range(5)]     # [0, 1, 4, 9, 16]

# Фильтрация с условием
evens = [x for x in range(10) if x % 2 == 0]  # [0, 2, 4, 6, 8]

# Преобразование элементов
words = ['hello', 'world', 'python']
upper_words = [word.upper() for word in words]  # ['HELLO', 'WORLD', 'PYTHON']
```

### Обход списков
```python
fruits = ['apple', 'banana', 'orange']

# Простой обход
for fruit in fruits:
    print(fruit)

# С индексом
for i, fruit in enumerate(fruits):
    print(f"{i}: {fruit}")

# Обход нескольких списков
prices = [1.2, 0.8, 1.5]
for fruit, price in zip(fruits, prices):
    print(f"{fruit}: ${price}")
```

### Проверка списков
```python
nums = [1, 2, 3, 4, 5]

# Проверки
is_all_positive = all(x > 0 for x in nums)  # True
is_any_negative = any(x < 0 for x in nums)  # False
is_empty = len(nums) == 0                   # False
```

## ⚠️ Частые ошибки

```python
# ❌ Неправильно - изменяется исходный список
original = [1, 2, 3]
modified = original
modified.append(4)
print(original)  # [1, 2, 3, 4] - изменился исходный!

# ✅ Правильно - создаем копию
original = [1, 2, 3]
modified = original.copy()
modified.append(4)
print(original)  # [1, 2, 3] - исходный не изменился

# ❌ Выход за границы
items = ['a', 'b', 'c']
# item = items[5]  # IndexError!

# ✅ Проверка длины
if len(items) > 5:
    item = items[5]
else:
    print("Индекс вне диапазона")
```

## 🎪 Встроенные функции для списков

```python
data = [3, 1, 4, 1, 5, 9, 2]

# Основные функции
length = len(data)      # 7
total = sum(data)       # 25
maximum = max(data)     # 9
minimum = min(data)     # 1
sorted_data = sorted(data)  # [1, 1, 2, 3, 4, 5, 9] (новая копия)

# Сортировка с ключом
words = ['apple', 'banana', 'cherry']
by_length = sorted(words, key=len)  # ['apple', 'cherry', 'banana']
```

## 🏆 Ключевые моменты для запоминания

- ✅ **Списки упорядоченные** - сохраняют порядок элементов
- ✅ **Списки изменяемые** - можно менять элементы после создания
- ✅ **Поддерживают дубликаты** - могут содержать повторяющиеся элементы
- ✅ **Индексируемые** - доступ к элементам по индексу `[0]`, `[1]`, etc.
- ✅ **Гибкие** - могут содержать элементы разных типов

---

**Используйте списки когда нужно:**
- Сохранить порядок элементов
- Хранить дубликаты
- Часто обращаться к элементам по индексу
- Последовательно обрабатывать данные
- Реализовывать стеки, очереди, коллекции
