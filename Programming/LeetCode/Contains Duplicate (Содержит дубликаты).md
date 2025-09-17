<span style="color:rgb(0, 176, 80)">**Easy**</span>

Для целочисленного массива `nums` верните `true` в случае, если какое-либо значение встречается в массиве **более одного раза**, в противном случае верните `false`.

**Пример 1:**

```java
Input: nums = [1, 2, 3, 3]

Output: true
```

**Пример 2:**

```java
Input: nums = [1, 2, 3, 4]

Output: false
```

Решение:
```python
class Solution:
	def hasDuplicate(self, nums: List[int]) -> bool:
		return sorted(set(nums)) != sorted(nums)
```
