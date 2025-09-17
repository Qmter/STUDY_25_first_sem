<span style="color:rgb(255, 192, 0)">**Medium**</span> 

Учитывая целочисленный массив `nums` и целое число `k`, верните `k` наиболее часто встречающихся элементов в массиве.

Тестовые примеры генерируются таким образом, чтобы ответ всегда был **уникальным**.

Вы можете возвращать выходные данные в **любом порядке**.

**Пример 1:**

```java
Input: nums = [1,2,2,3,3,3], k = 2

Output: [2,3]
```

Копировать

**Пример 2:**

```java
Input: nums = [7,7], k = 1

Output: [7]
```

Копировать

**Ограничения:**

- `1 <= nums.length <= 10^4`.
- `-1000 <= nums[i] <= 1000`
- `1 <= k <= number of distinct elements in nums`.


Решение:

```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        count = {}
        freq = [[] for i in range(len(nums) + 1)]

        for i in nums:
            count[i] = 1 + count.get(i, 0)

        for n, c in count.items():
            freq[c].append(n)

        res = []

        for i in range(len(freq) - 1, 0, -1):
            for n in freq[i]:
                res.append(n)
                if len(res) == k:
                    return res

        return res
```