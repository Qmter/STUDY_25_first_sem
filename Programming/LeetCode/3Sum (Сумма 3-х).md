<span style="color:rgb(255, 192, 0)">**Medium**</span> 

Учитывая массив целых чисел `nums`, верните все триплеты, `[nums[i], nums[j], nums[k]]` где `nums[i] + nums[j] + nums[k] == 0`, и все индексы `i`, `j` и `k` различны.

Результат _не должен_ содержать повторяющихся триплетов. Вы можете возвращать результат и триплеты в **любом порядке**.

**Пример 1:**

```java
Input: nums = [-1,0,1,2,-1,-4]

Output: [[-1,-1,2],[-1,0,1]]
```

Копировать

Объяснение:  
`nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.`  
`nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.`  
`nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.`  
Отдельные тройки — это `[-1,0,1]` и `[-1,-1,2]`.

**Пример 2:**

```java
Input: nums = [0,1,1]

Output: []
```

Копировать

Объяснение: единственный возможный триплет не даёт в сумме 0.

**Пример 3:**

```java
Input: nums = [0,0,0]

Output: [[0,0,0]]
```

Копировать

Объяснение: Сумма всех возможных троек равна 0.

**Ограничения:**

- `3 <= nums.length <= 1000`
- `-10^5 <= nums[i] <= 10^5`


Алгоритм:
1. Берем первое число.
2. Для массива после этого числа применяем алгоритм [[Two Integer Sum II (Сумма двух целых чисел II)]].
3. Находим все числа дающие в сумме 0.

Решение:

```python
class Solution:  
    def threeSum(self, nums: list[int]) -> list[list[int]]:  
  
        out = []  
        nums.sort()  
  
        for i, a in enumerate(nums):  
            if i > 0 and a == nums[i - 1]:  
                continue  
  
            l, r = i + 1, len(nums) - 1  
  
            while l < r:  
                threeSum = a + nums[l] + nums[r]  
  
                if threeSum < 0:  
                    l += 1  
                elif threeSum > 0:  
                    r -= 1  
                else:  
                    out.append([a, nums[l], nums[r]])  
                    l += 1  
                    while nums[l] == nums[l - 1] and l < r:  
                        l += 1  
  
        return out  
```