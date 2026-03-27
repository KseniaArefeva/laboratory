# Лабораторная №1
**Выполнила Арефьева Ксения Дмитриевна, ИДБ-25-07**

### 1. Проверка наличия элемента в массиве
Алгоритмическая сложность: O(n)

```python
def contains_item(collection, target):
    for item in collection:
        if item == target:
            return True
    return False
```
| n | Время (сек) |
|---|---|
| 10 | 0.00000380 |
| 100 | 0.00000650 |
| 1000 | 0.00003620 |
| 10000 | 0.00027150 |

### 2. Поиск предпоследнего максимального значения
Алгоритмическая сложность: O(n)
```python
def find_second_largest(numbers):
    if len(numbers) < 2:
        return False
    largest = second = numbers[0]
    for num in numbers:
        if num > largest:
            second = largest
            largest = num
        elif num > second and num != largest:
            second = num
    return second
```
| n | Время (сек) |
|---|---|
| 10 | 0.00000590 |
| 100 | 0.00000830 |
| 1000 | 0.00006920 |
| 10000 | 0.00061480 |

### 3. Двоичный поиск элемента
Алгоритмическая сложность: O(log n)
```python
def binary_search(data, target):
    sorted_data = sorted(data)
    left_bound, right_bound = 0, len(sorted_data) - 1
    while left_bound <= right_bound:
        middle = (right_bound + left_bound) // 2
        if target > sorted_data[middle]:
            left_bound = middle + 1
        elif target < sorted_data[middle]:
            right_bound = middle - 1
        else:
            return True
    return False
```
| n | Время (сек) |
|---|---|
| 10 | 0.00000920 |
| 100 | 0.00001380 |
| 1000 | 0.00020450 |
| 10000 | 0.00148930 |

### 4. Создание матрицы умножения
Алгоритмическая сложность: O(n²)
```python
def create_multiplication_matrix(dimension):
    matrix = []
    for row_idx in range(1, dimension + 1):
        current_row = []
        for col_idx in range(1, dimension + 1):
            current_row.append(row_idx * col_idx)
        matrix.append(current_row)
    return matrix
```
| n | Время (сек) |
|---|---|
| 10 | 0.00002910 |
| 50 | 0.00025180 |
| 100 | 0.00160340 |

### 5. Сортировка перемешиванием 
Алгоритмическая сложность: O(n²) в худшем случае, O(n) в лучшем

Пространственная сложность: O(n)
```python
def bidirectional_bubble_sort(elements):
    """
    Шейкерная сортировка (коктейльная сортировка)
    Проходит по массиву в обоих направлениях для оптимизации
    """
    elements = elements.copy()
    length = len(elements)
    left_boundary = 0
    right_boundary = length - 1
    is_sorted = False
    
    while not is_sorted and left_boundary < right_boundary:
        is_sorted = True
        
        # Проход слева направо - перемещаем максимальный элемент в конец
        for current_pos in range(left_boundary, right_boundary):
            if elements[current_pos] > elements[current_pos + 1]:
                elements[current_pos], elements[current_pos + 1] = \
                elements[current_pos + 1], elements[current_pos]
                is_sorted = False
        
        if is_sorted:
            break
            
        right_boundary -= 1
        is_sorted = True
        
        # Проход справа налево - перемещаем минимальный элемент в начало
        for current_pos in range(right_boundary - 1, left_boundary - 1, -1):
            if elements[current_pos] > elements[current_pos + 1]:
                elements[current_pos], elements[current_pos + 1] = \
                elements[current_pos + 1], elements[current_pos]
                is_sorted = False
        
        left_boundary += 1
    
    return elements
```
| n | Время (сек) |
|---|---|
| 10 | 0.00002150 |
| 100 | 0.00023480 |
| 1000 | 0.02456730 |
| 10000 | 2.14892340 |
