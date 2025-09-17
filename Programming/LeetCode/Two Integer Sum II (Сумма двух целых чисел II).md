<span style="color:rgb(255, 192, 0)">**Medium**</span> 

Дан массив целых чисел `numbers`, отсортированный в **неубывающем порядке**.

Верните индексы (**1-индексированные**) двух чисел `[index1, index2]`, сумма которых равна заданному целевому числу `target` и `index1 < index2`. Обратите внимание, что `index1` и `index2` не могут быть равны, поэтому вы не можете использовать один и тот же элемент дважды.

Всегда будет **ровно одно верное решение**.

Ваше решение должно использовать O(1)O(1) дополнительного пространства.

**Пример 1:**

```java
Input: numbers = [1,2,3,4], target = 3

Output: [1,2]
```

Копировать

Объяснение:  
Сумма 1 и 2 равна 3. Поскольку мы предполагаем, что массив индексируется с 1, `index1` = 1, `index2` = 2. Мы возвращаем `[1, 2]`.

**Ограничения:**

- `2 <= numbers.length <= 1000`
- `-1000 <= numbers[i] <= 1000`
- `-1000 <= target <= 1000`

Решение:

```python
class Solution:  
    def twoSum(self, numbers: list[int], target: int) -> list[int]:  
        out = []  
        i = 0  
        j = len(numbers) - 1  
  
        while i != j:  
            if numbers[i] + numbers[j] > target:  
                j -= 1  
                continue  
            elif numbers[i] + numbers[j] < target:  
                i += 1  
            else:  
                out.append(i + 1)  
                out.append(j + 1)  
                return out  
        return []
```