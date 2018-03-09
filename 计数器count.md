#计数器count()实现
##1.闭包(返回函数)实现
```python
def creatCount():
	f = [0]
	def count():
		f[0] += 1
		return f[0]
	return count
```
```python
def creatCount():
	i = 0
	def count():
		nonlocal i
		i += 1
		return i
	return count
```
##2.collections 模块实现
```python
from collections import defaultdict

c = defaultdict(0)
for ch in 'hello world!':
	c[ch] += 1

print(c)
```

```python
from collections import Counter

c = Counter()
for ch in 'hello world!':
	c[ch] += 1

print(c)

```
##dict子类实现

```python
class Counter(dict):
	def __missing__(self, key):
		return 0

c = Counter()
for ch in 'hello world!':
	c[ch] += 1

print(c)

```

##itertools模块实现
```python
import itertools

c = itertools.count(1)
for n in c:
	print(n)
```