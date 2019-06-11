# <img src="../../../images/icon/java.png" width="30" height="30" />HashMap

---

## 概述：

* **HashMap继承AbstractMap，实现了Map<K,V>, Cloneable, Serializable等接口**

* **HashMap的键和值对均可以为空，HashMap是无序的，键是不可以重复的，并且HashMap是非线程安全的**

* **HashMap1.8之前的底层结构是数组加链表，1.8之后引入了红黑树，在链表长度超过默认阈值的时候，链表将转换为红黑树**

* **HashMap中 Node[] table 的初始化长度是16，如果在给HashMap赋值的时候超过这个数量则会进行扩容扩容后的HashMap的长度是之前的两倍**

* **在并发多线程的场景中使用HashMap在需要进行扩容的时候可能会造成死锁，1.8之后，不会死锁，会出现部分空值，之前死锁的原因是应为扩容时
可能会出现环形链表，在get的时候死循环，所以死锁**

## put方法的逻辑

**hashTable是在put的时候进行初始化，并不是在构造的时候进行初始化**

```java
public V put(K key, V value) {
        return putVal(hash(key), key, value, false, true);
}

final V putVal(int hash, K key, V value, boolean onlyIfAbsent,
                   boolean evict) {
        Node<K,V>[] tab; Node<K,V> p; int n, i;
        //如果原table等于空，或者原来table的长度为0，则进行扩容（初始化）
        if ((tab = table) == null || (n = tab.length) == 0)
            n = (tab = resize()).length;
        //如果使用当前hash计算出来的下标没有值的话，直接进行插入
        if ((p = tab[i = (n - 1) & hash]) == null)
            tab[i] = newNode(hash, key, value, null);
        //如果有值
        else {
            Node<K,V> e; K k;
            //判断之前的值中的key是否与现在的key相同（同时判断key值的hash以及key是否相等），如果有，则进行覆盖
            if (p.hash == hash &&
                ((k = p.key) == key || (key != null && key.equals(k))))
                e = p;
            //判断是否是红黑树，如果是红黑树的话，进行红黑树操作，无旧值新增，有旧值，覆盖
            else if (p instanceof TreeNode)
                e = ((TreeNode<K,V>)p).putTreeVal(this, tab, hash, key, value);
            //链表，无旧值新增，有旧值，覆盖
            else {
                for (int binCount = 0; ; ++binCount) {
                    if ((e = p.next) == null) {
                        p.next = newNode(hash, key, value, null);
                        if (binCount >= TREEIFY_THRESHOLD - 1) // -1 for 1st
                            treeifyBin(tab, hash);
                        break;
                    }
                    if (e.hash == hash &&
                        ((k = e.key) == key || (key != null && key.equals(k))))
                        break;
                    p = e;
                }
            }
            if (e != null) { // existing mapping for key
                V oldValue = e.value;
                if (!onlyIfAbsent || oldValue == null)
                    e.value = value;
                afterNodeAccess(e);
                return oldValue;
            }
        }
        ++modCount;
        //判断是否需要扩容
        if (++size > threshold)
            resize();
        afterNodeInsertion(evict);
        return null;
}
```

1. 如果HashMap未被初始话，则进行初始化

2. 对Key的HashCode进行求Hash值，然后通过Table的长度以及Hash值计算下标，这个很重要，因为涉及到扩容，
如果Table的长度不参与下标的计算，那么扩容是没有意义的，因为无论你如何进行扩容，在计算下标的时候，无法
保证下标会计算到扩容之后的Table下标中去，当然，还有另外一个原因，在没有扩容的时候也无法保证计算出来的
下标，会在默认的长度中，不会越界

3. 如果没有碰撞，直接放入桶中

4. 发生碰撞，是否存在key值相同，如果相同，进行替换

5. 是否是红黑树，如果是，检查红黑树中是否存在相同key，如果有，进行替换，如果没有，进行添加

6. 是否是链表，如果是，检查链表中是否存在相同key，如果有，进行替换，如果没有，进行添加

7. 在链表的长度大于等于8-1并且hash桶的长度大于等于64的时候，会将链表进行树化

8. 在红黑树的节点小于等于6的时候，会将红黑树进行链表化

9. 超过阈值，进行扩容

![HashMap-Content](../../../images/java/base/hashmap/hashmap-content.jpg)

## 网络资源:

* **知乎：**[Java 8系列之重新认识HashMap](https://www.zhihu.com/search?type=content&q=HashMap)
* **知乎：**[HashMap源码分析（JDK 1.8）](https://www.zhihu.com/search?type=content&q=hashmap1.8%E6%BA%90%E4%BB%A3%E7%A0%81)
