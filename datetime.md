#datetime模块
##datetime转换为timestamp
在计算机中，时间实际上是用数字表示的。我们把1970年1月1日 00:00:00 UTC+00:00时区的时刻称为epoch time，记为0（1970年以前的时间timestamp为负数），当前时间就是相对于epoch time的秒数，称为timestamp。
`timestamp = 0 = 1970-1-1 00:00:00 UTC+0:00`
对应的北京时间是：
`timestamp = 0 = 1970-1-1 08:00:00 UTC+8:00`
可见**timestamp的值与时区毫无关系**，因为timestamp一旦确定，其UTC时间就确定了，转换到任意时区的时间也是完全确定的，这就是为什么计算机存储的当前时间是以timestamp表示的，因为全球各地的计算机在任意时刻的timestamp都是完全相同的（假定时间已校准）。
例如下面这个程序，时间为 '2015-1-21 9:01:30 UTC+5:00':
```python
from datetime import datetime, timedelta, timezone

cdays = datetime.strptime('2015-1-21 9:01:30', '%Y-%m-%d %H:%M:%S')
print('cdaystamp:',cdays.timestamp())
dt = cdays.replace(tzinfo = timezone(timedelta(hours = 5)))
print('dt5cdays:', dt.timestamp())
bj_dt = dt.astimezone(timezone(timedelta(hours = 8)))
print(bj_dt)
print('bjcdays:',bj_dt.timestamp())

```

输出结果都为：
cdaystamp: 1421802090.0
dt5cdays: 1421812890.0
2015-01-21 12:01:30+08:00
bjcdays: 1421812890.0
