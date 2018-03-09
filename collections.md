#collections
##namedtuple
collections.namedtuple(typename, field_names, verbose=False, rename=False)
```python
from collection import namedtuple

sjdu = namedtuple('point', ['x', 'y']) 
p = point(1, 2)  
'''
also can be p = point(x , y = 2) instantiate with positional or keyword arguments

or p = sjdu(1, 2)  the name of instance can be different from the typename

'''
>>> p[0] + p[1]  #indexable like the plain tuple (1, 2)
3
>>> a, b = p # unpack like a regular tuple
>>> a, b
(1, 2)
>>> p.x # fields also accessible by name
1 
>>> p #readable __repr__ with a name=value style
point(x = 1, y = 2)
```
可以验证创建的Point对象是tuple的一种子类：
```python
>>> isinstance(p, point)
True
>>> isinstance(p, tuple)
True

```
