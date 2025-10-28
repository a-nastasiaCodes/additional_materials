Отлично! Вот comprehensive шпаргалка по множествам в Python для студентов.

# 🎯 Шпаргалка по множествам в Python

## 📌 Основные понятия

**Множество** - неупорядоченная коллекция **уникальных** элементов
- ✅ **Быстрый поиск** - O(1) вместо O(n) в списках
- ✅ **Уникальность** - автоматическое удаление дубликатов
- ❌ **Нет порядка** - элементы хранятся в произвольном порядке
- ❌ **Нет индексов** - нельзя обратиться по индексу my_set[0]

## 🆚 Создание множеств

```python
# Пустое множество (только так!)
empty_set = set()
# empty_set = {}  # ❌ Это словарь!

# Множество с элементами
fruits = {'apple', 'banana', 'orange'}
numbers = {1, 2, 3, 4, 5}
mixed = {1, 'hello', 3.14, True}

# Из других коллекций
from_list = set([1, 2, 2, 3, 3])      # {1, 2, 3}
from_string = set('hello')            # {'h', 'e', 'l', 'o'}
from_range = set(range(5))            # {0, 1, 2, 3, 4}
from_tuple = set((1, 2, 3))           # {1, 2, 3}
```

## 🔧 Основные операции

### Добавление элементов
```python
items = {1, 2, 3}

items.add(4)           # {1, 2, 3, 4}
items.add(2)           # {1, 2, 3, 4} (дубликат не добавится)
items.update([5, 6])   # {1, 2, 3, 4, 5, 6} (добавить несколько)
items.update({7, 8})   # {1, 2, 3, 4, 5, 6, 7, 8}
```

### Удаление элементов
```python
items = {1, 2, 3, 4, 5}

items.remove(3)        # {1, 2, 4, 5} (KeyError если элемента нет)
items.discard(10)      # {1, 2, 4, 5} (не вызывает ошибку)
popped = items.pop()   # Удаляет случайный элемент (1), осталось {2, 4, 5}
items.clear()          # set() (полная очистка)
```

### Проверка элементов
```python
nums = {1, 2, 3, 4, 5}

2 in nums              # True (быстрая проверка!)
6 in nums              # False
len(nums)              # 5 (количество элементов)
```

## 📊 Математические операции

```python
A = {1, 2, 3, 4}
B = {3, 4, 5, 6}
```

### Объединение (union)
```python
union1 = A | B         # {1, 2, 3, 4, 5, 6}
union2 = A.union(B)    # {1, 2, 3, 4, 5, 6}
```

### Пересечение (intersection)
```python
intersection1 = A & B          # {3, 4}
intersection2 = A.intersection(B)  # {3, 4}
```

### Разность (difference)
```python
diff1 = A - B              # {1, 2} (в A, но не в B)
diff2 = B - A              # {5, 6} (в B, но не в A)
diff3 = A.difference(B)    # {1, 2}
```

### Симметрическая разность (symmetric difference)
```python
sym_diff1 = A ^ B                  # {1, 2, 5, 6} (элементы только в одном из множеств)
sym_diff2 = A.symmetric_difference(B)  # {1, 2, 5, 6}
```

## 🔍 Сравнение множеств

```python
X = {1, 2, 3}
Y = {1, 2}
Z = {1, 2, 3}

X == Z                  # True (равны)
X != Y                  # True (не равны)

Y <= X                  # True (Y подмножество X)
Y.issubset(X)           # True

X >= Y                  # True (X надмножество Y)
X.issuperset(Y)         # True

X.isdisjoint({4, 5})    # True (нет общих элементов)
```

## 💡 Практические примеры

### Удаление дубликатов
```python
# Быстрое удаление дубликатов из списка
duplicates = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
unique = list(set(duplicates))  # [1, 2, 3, 4]
```

### Проверка уникальности
```python
def all_unique(items):
    return len(items) == len(set(items))

all_unique([1, 2, 3])    # True
all_unique([1, 2, 2, 3]) # False
```

### Поиск общих элементов
```python
# Общие друзья в соцсетях
alice_friends = {'Bob', 'Charlie', 'Diana'}
bob_friends = {'Charlie', 'Diana', 'Eve'}

mutual_friends = alice_friends & bob_friends  # {'Charlie', 'Diana'}
```

### Валидация данных
```python
valid_statuses = {'active', 'pending', 'completed'}
user_status = 'active'

if user_status in valid_statuses:
    print("Статус корректен")
else:
    print(f"Неверный статус. Допустимые: {valid_statuses}")
```

## 🎪 Специальные методы

### Множества-компараторы
```python
A = {1, 2, 3}
B = {2, 3, 4}

A.intersection_update(B)    # A становится {2, 3} (A = A & B)
A.difference_update(B)      # A становится {1} (A = A - B)
A.update(B)                 # A становится {1, 2, 3, 4} (A = A | B)
```

### Неизменяемые множества
```python
# frozenset - неизменяемое множество
frozen = frozenset([1, 2, 3])
# frozen.add(4)  # ❌ AttributeError: нельзя изменить!

# Используется как ключ в словарях
valid_combinations = {
    frozenset(['admin', 'user']): 'full_access',
    frozenset(['guest']): 'read_only'
}
```

## 🚀 Продвинутые приемы

### Генераторы множеств
```python
# Аналогично генераторам списков
squares = {x**2 for x in range(5)}           # {0, 1, 4, 9, 16}
evens = {x for x in range(10) if x % 2 == 0} # {0, 2, 4, 6, 8}
words = {'hello', 'world', 'python'}
lengths = {len(word) for word in words}      # {5, 6}
```

### Фильтрация данных
```python
# Быстрая фильтрация с помощью множеств
all_products = {'laptop', 'phone', 'tablet', 'watch'}
available_products = {'laptop', 'phone', 'headphones'}

out_of_stock = all_products - available_products  # {'tablet', 'watch'}
new_products = available_products - all_products  # {'headphones'}
```

### Группировка по уникальным значениям
```python
# Быстрый поиск уникальных категорий
products = [
    {'name': 'laptop', 'category': 'electronics'},
    {'name': 'phone', 'category': 'electronics'},
    {'name': 'book', 'category': 'education'},
    {'name': 'phone', 'category': 'electronics'}  # Дубликат
]

categories = {product['category'] for product in products}
# {'electronics', 'education'}
```

## ⚡ Производительность

```python
# Множества vs Списки (поиск элемента)
large_list = list(range(100000))
large_set = set(large_list)

# Мгновенно (O(1))
99999 in large_set

# Медленно (O(n))
99999 in large_list
```

## ⚠️ Ограничения и особенности

### Что можно хранить в множествах
```python
# ✅ Хешируемые (неизменяемые) типы
valid_set = {1, 'hello', 3.14, True, (1, 2)}  # Кортеж - ок

# ❌ Нехешируемые (изменяемые) типы
# invalid_set = {[1, 2]}          # TypeError: список
# invalid_set = {{1, 2}}          # TypeError: множество
# invalid_set = {{'a': 1}}        # TypeError: словарь
```

### Порядок элементов
```python
# Порядок не гарантируется!
items = {3, 1, 4, 1, 5, 9, 2}
print(items)  # Может быть {1, 2, 3, 4, 5, 9} или в другом порядке
```

## 🎯 Когда использовать множества?

### ✅ ИСПОЛЬЗУЙТЕ множества когда:
- Нужно проверить наличие элемента (быстрый поиск)
- Нужно удалить дубликаты
- Выполняются математические операции (объединение, пересечение)
- Порядок элементов не важен
- Данные по природе уникальны (ID, email, username)

### ❌ НЕ ИСПОЛЬЗУЙТЕ множества когда:
- Важен порядок элементов
- Нужны дубликаты
- Нужен доступ по индексу
- Храните изменяемые объекты

## 📝 Быстрые рецепты

```python
# Быстрая проверка пересечения
if set(list1) & set(list2):
    print("Есть общие элементы!")

# Все элементы уникальны?
is_unique = len(items) == len(set(items))

# Быстрое преобразование без дубликатов
unique_list = list(set(duplicate_list))

# Найти элементы, которые есть только в одном из списков
only_in_one = set(list1) ^ set(list2)
```

---
