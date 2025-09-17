<span style="color:rgb(0, 176, 80)">**Easy**</span>

Дан массив целых чисел `nums` и целое число `target`. Найдите индексы `i` и `j` такие, что `nums[i] + nums[j] == target` и `i != j`.

Вы можете предположить, что _каждый_ входной сигнал содержит ровно одну пару индексов `i` и `j`, удовлетворяющих условию.

Сначала верните ответ с меньшим индексом.

**Пример 1:**

```java
Input: 
nums = [3,4,5,6], target = 7

Output: [0,1]
```

Копировать

Объяснение: `nums[0] + nums[1] == 7`, поэтому мы возвращаем `[0, 1]`.

**Пример 2:**

```java
Input: nums = [4,5,6], target = 10

Output: [0,2]
```

Копировать

**Пример 3:**

```java
Input: nums = [5,5], target = 10

Output: [0,1]
```

Копировать

**Ограничения:**

- `2 <= nums.length <= 1000`
- `-10,000,000 <= nums[i] <= 10,000,000`
- `-10,000,000 <= target <= 10,000,000`


Решение:

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        prevMap = {}
        for i, val in enumerate(nums):
            tmp = target - nums[i]
            if tmp in prevMap:
                return [prevMap[tmp], i]
            prevMap[val] = i
        return []
```