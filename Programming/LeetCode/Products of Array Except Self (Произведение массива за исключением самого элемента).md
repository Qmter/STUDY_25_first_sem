<span style="color:rgb(255, 192, 0)">**Medium**</span> 

Для заданного целочисленного массива `nums` верните массив `output`, где `output[i]` — произведение всех элементов `nums` за исключением `nums[i]`.

Каждый продукт **гарантированно** помещается в **32-битное** целое число.

Вопрос: можете ли вы решить эту задачу за O(n)O(n) времени, не используя операцию деления?

**Пример 1:**

```java
Input: nums = [1,2,4,6]

Output: [48,24,12,8]
```

Копировать

**Пример 2:**

```java
Input: nums = [-1,0,1,2,3]

Output: [0,-6,0,0,0]
```

Копировать

**Ограничения:**

- `2 <= nums.length <= 1000`
- `-20 <= nums[i] <= 20`


Решение:

```python
class Solution:
	def productExceptSelf(self, nums: List[int]) -> List[int]:
		pre = 1
		post = 1
		out = [0] * len(nums)

		for i in range(len(nums)):
			if i == 0:
				out[i] = pre
				pre *= nums[i]
			else:
				out[i] = pre
				pre *= nums[i]  
		
		for i in range(len(nums) - 1, -1, -1):
			if i == len(nums) - 1:
				post *= nums[i]		
			else:
				out[i] *= post
				post *= nums[i]
		
		return out
```