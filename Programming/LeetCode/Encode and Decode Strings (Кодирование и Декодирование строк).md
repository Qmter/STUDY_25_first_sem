<span style="color:rgb(255, 192, 0)">**Medium**</span> 

Разработайте алгоритм для кодирования списка строк в одну строку. Затем закодированная строка декодируется обратно в исходный список строк.

Пожалуйста, реализуйте `encode` и `decode`

**Пример 1:**

```java
Input: ["neet","code","love","you"]

Output:["neet","code","love","you"]
```

Копировать

**Пример 2:**

```java
Input: ["we","say",":","yes"]

Output: ["we","say",":","yes"]
```

Копировать

**Ограничения:**

- `0 <= strs.length < 100`
- `0 <= strs[i].length < 200`
- `strs[i]` содержит только символы UTF-8.


Решение:

```python
class Solution:
    
    def encode(self, strs: List[str]) -> str:
        res = ""
        for s in strs:
            res += str(len(s)) + "#" + s
        return res

    def decode(self, s: str) -> List[str]:
        res = []
        i = 0
        
        while i < len(s):
            j = i
            while s[j] != '#':
                j += 1
            length = int(s[i:j])
            i = j + 1
            j = i + length
            res.append(s[i:j])
            i = j
            
        return res
```