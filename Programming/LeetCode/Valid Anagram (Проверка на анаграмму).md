<span style="color:rgb(0, 176, 80)">**Easy**</span>

Даны две строки `s` и `t`, верните `true` в случае, если эти две строки являются анаграммами друг друга, в противном случае верните `false`.

**Анаграмма** — это строка, содержащая те же символы, что и другая строка, но в другом порядке.

**Пример 1:**

```java
Input: s = "racecar", t = "carrace"

Output: true
```

Копировать

**Пример 2:**

```java
Input: s = "jar", t = "jam"

Output: false
```

Копировать

**Ограничения:**

- `s` и `t` состоят из строчных букв английского алфавита.


Решение:

```python
class Solution:
	def isAnagram(self, s: str, t: str) -> bool:
		return sorted(s) == sorted(t)
```