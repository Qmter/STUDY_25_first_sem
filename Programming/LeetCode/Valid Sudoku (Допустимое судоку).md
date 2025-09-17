<span style="color:rgb(255, 192, 0)">**Medium**</span> 

Вам дана таблица `9 x 9` Судоку `board`. Таблица Судоку считается правильной, если соблюдены следующие правила:

1. Каждая строка должна содержать цифры `1-9` без повторений.
2. Каждый столбец должен содержать цифры `1-9` без дубликатов.
3. Каждый из девяти `3 x 3` блоков в сетке должен содержать цифры `1-9` без дубликатов.

Верните `true` в случае, если Судоку заполнено правильно, иначе верните `false`

Примечание: для того чтобы доска считалась действительной, она не обязательно должна быть полной или решаемой.

**Пример 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/0be40c5d-2d18-42b8-261b-13ca50de4100/public)

```java
Input: board = 
[["1","2",".",".","3",".",".",".","."],
 ["4",".",".","5",".",".",".",".","."],
 [".","9","8",".",".",".",".",".","3"],
 ["5",".",".",".","6",".",".",".","4"],
 [".",".",".","8",".","3",".",".","5"],
 ["7",".",".",".","2",".",".",".","6"],
 [".",".",".",".",".",".","2",".","."],
 [".",".",".","4","1","9",".",".","8"],
 [".",".",".",".","8",".",".","7","9"]]

Output: true
```

Копировать

**Пример 2:**

```java
Input: board = 
[["1","2",".",".","3",".",".",".","."],
 ["4",".",".","5",".",".",".",".","."],
 [".","9","1",".",".",".",".",".","3"],
 ["5",".",".",".","6",".",".",".","4"],
 [".",".",".","8",".","3",".",".","5"],
 ["7",".",".",".","2",".",".",".","6"],
 [".",".",".",".",".",".","2",".","."],
 [".",".",".","4","1","9",".",".","8"],
 [".",".",".",".","8",".",".","7","9"]]

Output: false
```

Копировать

Объяснение: в верхнем левом квадрате 3x3 есть две единицы.

**Ограничения:**

- `board.length == 9`
- `board[i].length == 9`
- `board[i][j]` является цифрой `1-9` или `'.'`.



Решение:

1) С использованием [[collections — Типы данных контейнеров]] (не нужна ручная проверка на наличие ключа):

```python 
class Solution:  
    def isValidSudoku(self, board: list[list[str]]) -> bool:  
        row = collections.defaultdict(set)
        col = collections.defaultdict(set)  
        squares = collections.defaultdict(set)
          
        for r in range(len(board)):  
            for c in range(len(board)):  
                if board[r][c] == '.':  
                    continue  
                if (board[r][c] in row[r] or  
                        board[r][c] in col[c] or  
                        board[r][c] in squares[(r // 3, c // 3)]):  
                    return False  
  
                col[c].add(board[r][c])  
                row[r].add(board[r][c])  
                squares[(r // 3, c // 3)].add(board[r][c])  
  
        return True
```


2) С обычными словарями (нужна ручная проверка на наличие ключа)

```python
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        row = {}
        col = {}  
        squares = {} 

        for r in range(len(board)):
            for c in range(len(board)):
                if board[r][c] == '.':
                    continue

                # Проверяем, есть ли ключ в словаре, если нет — создаём множество
                if r not in row:
                    row[r] = set()
                if c not in col:
                    col[c] = set()
                if (r // 3, c // 3) not in squares:
                    squares[(r // 3, c // 3)] = set()

                if (board[r][c] in row[r] or
                    board[r][c] in col[c] or
                    board[r][c] in squares[(r // 3, c // 3)]):
                    return False

                row[r].add(board[r][c])
                col[c].add(board[r][c])
                squares[(r // 3, c // 3)].add(board[r][c])

        return True
```