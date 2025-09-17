<span style="color:rgb(255, 192, 0)">**Medium**</span> 

Учитывая массив строк `strs`, сгруппируйте все _анаграммы_ в под-списки. Вы можете вернуть результат в **любом порядке**.

**Анаграмма** — это строка, содержащая те же символы, что и другая строка, но в другом порядке.

**Пример 1:**

```java
Input: strs = ["act","pots","tops","cat","stop","hat"]

Output: [["hat"],["act", "cat"],["stop", "pots", "tops"]]
```

Копировать

**Пример 2:**

```java
Input: strs = ["x"]

Output: [["x"]]
```

Копировать

**Пример 3:**

```java
Input: strs = [""]

Output: [[""]]
```

Копировать

**Ограничения:**

- `1 <= strs.length <= 1000`.
- `0 <= strs[i].length <= 100`
- `strs[i]` состоит из строчных букв английского алфавита.


Решение:

Для решения понадобится алгоритм нахождения анаграмм - [[Valid Anagram (Проверка на анаграмму)]]

```python
class Solution:  
    def groupAnagrams(self, strs: list[str]) -> list[list[str]]:  
        d = {}  
  
        for i in strs:  
            st = ''.join(x for x in sorted(i))  
            if st not in d:  
                d[st] = [i]  
            else:  
                d[st].append(i)  
  
        return list(d.values())
```