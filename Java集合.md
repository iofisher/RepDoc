
[Java集合类: Set、List、Map、Queue使用场景梳理](http://www.cnblogs.com/LittleHann/p/3690187.html)：

![集合框架图](http://dl2.iteye.com/upload/attachment/0085/6119/74043b0f-2712-3105-ad99-17e5820e9457.jpg)  

Set集合类的编程应用场景：
> 1) HashSet的性能总是比TreeSet好(特别是最常用的添加、查询元素等操作)，因为TreeSet需要额外的红黑树算法来维护集合元素的次序。只有当需要一个保持排序的Set时，才应该使用TreeSet，否则都应该使用HashSet  
2) 对于普通的插入、删除操作，LinkedHashSet比HashSet要略慢一点，这是由维护链表所带来的开销造成的。不过，因为有了链表的存在，遍历LinkedHashSet会更快  
3) EnumSet是所有Set实现类中性能最好的，但它只能保存同一个枚举类的枚举值作为集合元素  
4) HashSet、TreeSet、EnumSet都是"线程不安全"的，通常可以通过Collections工具类的synchronizedSortedSet方法来"包装"该Set集合。
SortedSet s = Collections.synchronizedSortedSet(new TreeSet(...));          
        

List集合类的编程应用场景：
> 1. java提供的List就是一个"线性表接口"，ArrayList(基于数组的线性表)、LinkedList(基于链的线性表)是线性表的两种典型实现
2. Queue代表了队列，Deque代表了双端队列(既可以作为队列使用、也可以作为栈使用)
3. 因为数组以一块连续内存来保存所有的数组元素，所以数组在随机访问时性能最好。所以的内部以数组作为底层实现的集合在随机访问时性能最好。
4. 内部以链表作为底层实现的集合在执行插入、删除操作时有很好的性能
5. 进行迭代操作时，以链表作为底层实现的集合比以数组作为底层实现的集合性能好


Map集合类的编程应用场景：
> 1) HashMap和Hashtable的效率大致相同，因为它们的实现机制几乎完全一样。但HashMap通常比Hashtable要快一点，因为Hashtable需要额外的线程同步控制  
2) TreeMap通常比HashMap、Hashtable要慢(尤其是在插入、删除key-value对时更慢)，因为TreeMap底层采用红黑树来管理key-value对  
3) 使用TreeMap的一个好处就是： TreeMap中的key-value对总是处于有序状态，无须专门进行排序操作        

[Java Collections Tutorial](http://tutorials.jenkov.com/java-collections/index.html)(jenkov.com, 简单介绍)  
[The Java™ Tutorials](https://docs.oracle.com/javase/tutorial/collections/interfaces/index.html)(Collection)  
![](https://docs.oracle.com/javase/tutorial/figures/collections/colls-coreInterfaces.gif)    


[Java中的CopyOnWrite容器](http://coolshell.cn/articles/11175.html)  
使用CopyOnWriteMap需要注意两件事情:减少扩容开销、使用批量添加（因为每次添加，容器每次都会进行复制）；  
CopyOnWrite的缺点：内存占用问题、数据一致性问题（最终一致性）

[Java集合框架常用类对比总结](http://www.binky.cn/article/13787.html)






