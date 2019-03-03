# <img src="../../../images/icon/java.png" width="30" height="30" />Collection

---

## List概述

* 有序，元素存储和取出的顺序

* 可重复

* 可通过索引操作元素

* List的实现分为链表实现和数组实现：

    1. 链表的具体实现：
        
        * LinkedList的底层是链表进行实现的，查询慢，但是增删慢，线程不安全，效率较高。
        
    2. 数组的实现：
        
        * ArrayList的底层是使用数组进行实现的，查询快，但是增删慢，线程不安全，效率较高。
        
        * Vector的底层是使用数组进行实现的，线程安全，效率低。
        
## set概述

* 无序，元素的存储和取出的顺序

* 不可重复，元素唯一

* set的实现分为哈希表和二叉树

    1. hashSet是哈希表实现的set：
    
        * 保证元素的唯一性质，通过hashCode()和equals()
        
    2. treeSet是二叉树实现的set：
    
        * 保证元素排序；可以让对象所属的类去实现comparable接口，无参构造。可以实现比较器接口comparator，带参构造