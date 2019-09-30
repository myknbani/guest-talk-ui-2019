### The good news (1/3)

- Many complicated programming tasks can be solved without direct loops
- If you've taken database classes
  * you must have encountered a declarative language

```sql
SELECT post.* FROM users AS user
INNER JOIN posts AS post ON user.id = post.author_id
WHERE user.vip = TRUE -- searching
ORDER BY post.created_at DESC -- sorting
```

---

### The good news (2/3)

- The industry love declarative programming

<img alt="MLS" src="images/mls.jpg" style="width: 800px; height: 450px" />

---

### The good news (3/3)

- More of the left, less of the right 

<img alt="dumb" src="images/dumb.png" style="width: 800px; height: 450px" />

---

### What is declarative programming?

- Declarative: tells the computer **what** you want, without saying how
  
I want a cup of coffee!

# ☕

---

### What is imperative programming?

- Imperative: tells the computer **how**, step by step
  * Get a cup from the cupboard
  * Turn towards the dining table
  * Walk 7 steps
  * Put the cup on the table, 4 inches from the edge
  * Turn towards the coffee maker
  * Put 2 scoops of coffee granules on the machine
  * Put 2 cups of water on the reservior
  * Wait 25 seconds
  * SPOILER: <span style="color: white">
     forgot to press the switch, and you slipped!
    </span>

---

### Imperative Code

```python
>>> numbers = [3, 7, 2, 10, 5, 9, 13]
>>> count = 0
>>> total = 0
>>> while count < len(numbers):
...     total += numbers[count]
...     count += 1
...
>>> total
49
```

### Declarative Code

```python
>>> numbers = [3, 7, 2, 10, 5, 9, 13]
>>> sum(numbers)
49
```