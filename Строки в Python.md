## 1. Базовое определение и синтаксис

### 1.1. Основные способы определения строк
```python
# 1. Двойные кавычки
message = "Hello World!"

# 2. Одинарные кавычки
name = 'Tom'
```

### 1.2. Длинные строки с переносом
```python
# Перенос с использованием круглых скобок
text = ("Laudate omnes gentes laudate "
        "Magnificat in secula ")
```

### 1.3. Многострочные строки
```python
'''
Это КОММЕНТАРИЙ (если не присвоен переменной)
'''

text = '''Laudate omnes gentes laudate
Magnificat in secula
Et anima mea laudate
Magnificat in secula 
'''
# ВАЖНО: Тройные одинарные кавычки - это строка, если присвоены переменной
```

## 2. Управляющие последовательности (Escape Sequences)

### 2.1. Основные управляющие последовательности
| Последовательность | Назначение                        | Пример               |
|-------------------|-----------------------------------|----------------------|
| `\\`              | Обратный слеш                     | `"C:\\folder"`       |
| `\'`              | Одинарная кавычка                 | `'It\'s mine'`       |
| `\"`              | Двойная кавычка                   | `"He said \"Hi\""`   |
| `\n`              | Перенос строки                    | `"Line1\nLine2"`     |
| `\t`              | Табуляция (4 пробела)             | `"Name:\tJohn"`      |

```python
# Пример использования
text = "Message:\n\"Hello World\""
# Результат:
# Message:
# "Hello World"
```

### 2.2. Проблема с путями файлов
```python
# ПРОБЛЕМА: нежелательная интерпретация \n как переноса строки
path = "C:\python\name.txt"
print(path)  # Вывод: C:\python\n ame.txt (с переносом)

# РЕШЕНИЕ: использование сырых строк (raw strings)
path = r"C:\python\name.txt"
print(path)  # Вывод: C:\python\name.txt (корректно)
```

## 3. Форматирование строк

### 3.1. F-строки (форматированные строки)
```python
userName = "Tom"
userAge = 37
user = f"name: {userName}  age: {userAge}"
# Результат: "name: Tom  age: 37"
```

## 4. Индексация и доступ к символам

### 4.1. Прямая индексация
```python
string = "hello world"
c0 = string[0]   # 'h' (индексация с 0)
c6 = string[6]   # 'w'
# c11 = string[11]  # ОШИБКА: IndexError (выход за пределы)
```

### 4.2. Обратная индексация
```python
string = "hello world"
c1 = string[-1]  # 'd' (последний символ)
c5 = string[-5]  # 'w' (пятый с конца)
```

### 4.3. Неизменяемость строк
```python
string = "hello world"
# string[1] = "R"  # ОШИБКА: строки неизменяемы
# Можно только полностью переопределить:
string = "Hello world"  # Корректно
```

## 5. Итерация по строке
```python
string = "hello world"
for char in string:
    print(char)  # Вывод каждого символа по отдельности
```

## 6. Срезы (подстроки)

### 6.1. Основные формы срезов
```python
string = "hello world"

# Форма 1: string[:end]
sub_string1 = string[:5]      # "hello" (с 0 до 5, не включая 5)

# Форма 2: string[start:end]
sub_string2 = string[2:5]     # "llo" (со 2 до 5, не включая 5)

# Форма 3: string[start:end:step]
sub_string3 = string[2:9:2]   # "lowr" (с 2 до 9 через шаг 2)
```

### 6.2. Расширенные примеры срезов
```python
# Полная копия строки
copy = string[:]

# Инвертирование строки
reverse = string[::-1]  # "dlrow olleh"

# Каждый второй символ
every_second = string[::2]  # "hlowrd"
```

## 7. Операции со строками

### 7.1. Конкатенация (объединение)
```python
# Базовый вариант
fullname = "Tom" + " " + "Smith"  # "Tom Smith"

# С участием чисел (требуется явное преобразование)
age = 33
info = "Age: " + str(age)  # "Age: 33"
```

### 7.2. Повторение
```python
print("a" * 3)   # "aaa"
print("he" * 4)  # "hehehehe"
```

## 8. Сравнение строк

### 8.1. Лексикографический порядок
**Правила сравнения:**
1. Цифровые символы < Заглавные буквы < Строчные буквы
2. Сравнение идет посимвольно слева направо

```python
str1 = "1a"
str2 = "aa"
str3 = "Aa"

print(str1 > str2)  # False (цифра '1' < буквы 'a')
print(str2 > str3)  # True (строчная 'a' > заглавной 'A')
print("ba" > "ca")  # False ('b' < 'c')
```

### 8.2. Регистронезависимое сравнение
```python
str1 = "Tom"
str2 = "tom"

print(str1 == str2)                   # False (разный регистр)
print(str1.lower() == str2.lower())   # True (приведены к одному регистру)
print(str1.upper() == str2.upper())   # True (аналогично)
```

## 9. Функции для работы со строками

### 9.1. Основные функции
```python
# ord() - код символа в Unicode
print(ord("A"))     # 65
print(ord("a"))     # 97

# len() - длина строки
text = "hello world"
print(len(text))    # 11
```

### 9.2. Методы преобразования регистра
```python
text = "Hello World"
print(text.lower())  # "hello world"
print(text.upper())  # "HELLO WORLD"
```

## 10. Поиск в строках

### 10.1. Проверка вхождения
```python
text = "hello world"

# Оператор in (существует ли подстрока)
exist = "hello" in text      # True
exist = "world" in text      # True
exist = "sword" in text      # False

# Оператор not in (отсутствует ли подстрока)
not_exist = "hello" not in text  # False
not_exist = "sword" not in text  # True
```

## 11. Особые случаи и предупреждения

### 11.1. Тройные кавычки: строка vs комментарий
```python
# Это КОММЕНТАРИЙ (не присваивается переменной)
'''
Многострочный комментарий
Три одинарные кавычки
'''

# Это СТРОКА (присваивается переменной)
text = '''
Многострочная строка
Три одинарные кавычки
'''
```

### 11.2. Проблемы с путями в Windows
```python
# НЕПРАВИЛЬНО (из-за \n и \t):
path = "C:\new_folder\table.txt"
# Интерпретируется как: C:[newline]ew_folder[tab]able.txt

# ПРАВИЛЬНЫЕ варианты:
path1 = r"C:\new_folder\table.txt"      # Сырая строка
path2 = "C:\\new_folder\\table.txt"     # Двойные слеши
path3 = "C:/new_folder/table.txt"       # Unix-стиль (Python понимает)
```

### 11.3. Конкатенация с числами
```python
# ОШИБКА:
# age = 25
# text = "Age: " + age  # TypeError!

# ПРАВИЛЬНО:
age = 25
text = "Age: " + str(age)  # Явное преобразование
# ИЛИ через f-строку:
text = f"Age: {age}"       # Предпочтительный способ
```
