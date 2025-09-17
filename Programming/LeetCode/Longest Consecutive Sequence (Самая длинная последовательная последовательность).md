<span style="color:rgb(255, 192, 0)">**Medium**</span> 

Для заданного массива целых чисел `nums` верните _длину_ самой длинной последовательности элементов, которую можно сформировать.

_Последовательная последовательность_ — это последовательность элементов, в которой каждый элемент ровно `1` больше предыдущего. Элементы _не обязательно_ должны быть последовательными в исходном массиве.

Вы должны написать алгоритм, который выполняется за `O(n)` секунд.

**Пример 1:**

```java
Input: nums = [2,20,4,10,3,4,5]

Output: 4
```

Копировать

Объяснение: самая длинная последовательность символов — `[2, 3, 4, 5]`.

**Пример 2:**

```java
Input: nums = [0,3,2,5,4,6,1,1]

Output: 7
```

Копировать

**Ограничения:**

- `0 <= nums.length <= 1000`
- `-10^9 <= nums[i] <= 10^9`

Решение:

```python
class Solution:
	def longestConsecutive(self, nums: List[int]) -> int:
		num_set = set(nums)
		longest = 0  
		
		for num in num_set:
			if num - 1 not in num_set:
			current_num = num
			current_streak = 1	  
		
			while current_num + 1 in num_set:
				current_num += 1
				current_streak += 1
		
		longest = max(longest, current_streak)
		
		return longest
```