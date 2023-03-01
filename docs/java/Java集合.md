
# Collection

## Set

代表无序的，元素不可重复的集合。

## List

代表有序的，元素可以重复的集合。

## Queue

代表先进先出（FIFO）的队列。

# Map

代表具有映射关系（key-value）的集合

## HashMap

### put 过程

1.  首次扩容：
	先判断数组是否为空，若数组为空则进行第一次扩容（resize）；
2.  计算索引：
    通过hash算法，计算键值对在数组中的索引；
3.  插入数据：
    -   如果当前位置元素为空，则直接插入数据；
    -   如果当前位置元素非空，且key已存在，则直接覆盖其value；
    -   如果当前位置元素非空，且key不存在，则将数据链到链表末端；
    -   若链表长度达到8，则将链表转换成红黑树，并将数据插入树中；
4.  再次扩容
    如果数组中元素个数（size）超过threshold，则再次进行扩容操作。

## Hashtable

和HashMap类很相似，但是它支持同步。

## LinkedHashMap

按插入顺序排序。

## TreeMap

key按自然顺序排列甚至是自定义顺序排列。

## ConcurrentHashMap

put时采用分段锁/CAS的加锁机制

# 高效并发访问的集合类

## Concurrent开头

代表了支持并发访问的集合。

## CopyOnWrite开头

复制底层数组的方式来实现写操作。