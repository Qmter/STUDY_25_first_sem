<span style="color:rgb(255, 192, 0)">**Medium**</span> 

Вам дан целочисленный массив `heights`, где `heights[i]` обозначает высоту ithith-столбика.

Вы можете выбрать любые два бруска для формирования контейнера. Верните _максимальное_ количество воды, которое может вместить контейнер.


![[Pasted image 20250616122739.png]]


**Пример 1:**

```java
Input: height = [1,7,2,5,4,7,3,6]

Output: 36
```


**Пример 2:**

```java
Input: height = [2,2,2]

Output: 4
```



**Ограничения:**

- `2 <= height.length <= 1000`
- `0 <= height[i] <= 1000`


Решение:
<span style="color:rgb(240, 71, 71)">
**$$O(n^2):$$**
</span>

```python
class Solution:  
    def maxArea(self, heights: list[int]) -> int:  
        res = 0  
  
        for l in range(len(heights)):  
            for r in range(l + 1, len(heights)):  
                area = (r - l) * min(heights[l], heights[r])  
  
                res = max(res, area)  
  
        return res
```

<span style="color:rgb(0, 176, 80)">**$$O(n)$$**</span>
```python 
class Solution:  
    def maxArea(self, heights: list[int]) -> int:  
        res = 0  
  
        l = 0  
        r = len(heights) - 1  
  
        while l < r:  
            area = (r - l) * min(heights[l], heights[r])  
            res = max(area, res)  
            if heights[l] > heights[r]:  
                r -= 1  
            else:  
                l += 1  
  
        return res
```

host

```minicom
host (any | <A.B.C.D> | <ipv6_address>)
```

Используйте эту команду, чтобы установить адрес для приема запросов REST API.

#### Субкоманды

| Имя   | Описание       |
| ----- | -------------- |
| `any` | Любой IP адрес |

#### Параметры

| Имя            | Тип      | Описание              |
| -------------- | -------- | --------------------- |
| `A.B.C.D`      | A.B.C.D  | Конкретный адрес IPv4 |
| `ipv6_address` | X:X::X:X | Конкретный адрес IPv6 |

