# 数据结构与算法
## 线性表
### 基础概念
**数据结构：**

- 是相互之间存在一种或多种关系的数据元素的集合。

**逻辑结构和物理结构** 

- 关于数据结构，我们可以从逻辑结构和物理结构这两个维度去描述

**逻辑结构是数据对象中数据元素之间的关系**，是从逻辑意义上去描述的数据之间的组织形式。

逻辑结构有4种：

- 集合结构（数据元素之间仅以集合的方式体现，元素之间没有别的关系）

- 线性结构（数据元素之间存在一对一的关系）

- 树（数据元素之间为一对多或多对一的关系）

- 图（数据元素之间为多对多的关系）

**物理结构则是逻辑结构在计算机中内存中的存储形式**，分为两种：

- 顺序存储结构
- 链式存储结构

### 线性表
**线性表是零个或多个数据元素的的有限序列**

线性表是线性结构，元素之间存在一对一的关系，线性表可通过**顺序和链式**两种方式来实现。

顺序存储结构，是用一段**地址连续的存储单元依次存储线性表的数据元素**

链式存储结构，**用一组任意的存储单元来存储数据元素，不要求物理存储单元的连续性**，由一系列结点组成，每个结点除了要存储数据外，**还需存储指向后继结点或前驱结点的存储地址。**

### 顺序存储和链式存储对比

- 顺序存储结构
  - 优点
    - 实现比较简单
    - 查找指定位置的元素效率很快，时间复杂度为常数阶O(1)　
    - 无需额外存储元素之间的逻辑关系（链式存储由于存储空间随机分配，需要存储元素之间的逻辑关系）
  - 缺点
    - 需要预先分配存储空间，如果数据元素数量变化较大，很难确定存储容量，并导致空间浪费
    - 若频繁进行插入删除操作，则可能需要频繁移动大量数据元素

- 链式存储结构
  - 优点
    - 不需要提前分配存储空间，元素个数不受限制
    - 对于插入删除操作，在已找到目标位置前提下，效率很高，仅需处理元素之间的引用关系，时间复杂度为O(1)
  - 缺点
    - 实现相对复杂
    - 查找效率较低，最坏情况下需要遍历整张表
    - 由于物理存储位置不固定，需要额外存储数据元素之间的逻辑关系

### 代码实现
单链表
双端链表
双向链表
见`MyLinkedList.java`

**注意： **在过程中需要同时保持对结点的前驱结点和后继结点的引用，删除操作时，需要注意解除废弃结点的各种引用，便于GC。

## 二叉树
### 基础概念

**二叉树**(binary tree)是一棵树，其中每个结点都不能有多于两个儿子。

**二叉排序树**或者是一棵空树，或者是具有下列性质的二叉树：
- 若左子树不空，则左子树上所有结点的值均小于或等于它的根结点的值；
- 若右子树不空，则右子树上所有结点的值均大于或等于它的根结点的值；
- 左、右子树也分别为二叉排序树；

**二叉树的遍历**
二叉树的遍历是指从根节点出发，按照某种次序依次访问二叉树中所有结点，使得每个结点被访问一次且仅被访问一次。
二叉树的遍历方式有很多，主要有**前序遍历，中序遍历，后序遍历。**

**前序遍历**：

**前序遍历的规则是：若二叉树为空，则空操作返回，否则先访问根节点，然后前序遍历左子树，再前序遍历右子树**

**中序遍历**

**中序遍历的规则是:若树为空，则空操作返回；否则从根节点开始（注意并不是先访问根节点），中序遍历根节点的左子树，然后是访问根节点，最后中序遍历右子树。可以看到，如果是二叉排序树，中序遍历的结果就是个有序序列。**

**后序遍历**

**后序遍历的规则是:若树为空，则空操作返回；然后先遍历左子树，再遍历右子树，最后访问根结点，在遍历左、右子树时，仍然先遍历左子树，然后遍历右子树，最后遍历根结点。**

### 删除结点

对于二叉排序树的其他操作，比如插入，遍历等，比较容易理解；而删除操作相对复杂些。对于要删除的结点，有以下三种情况：

1. **叶子结点；**
2. **仅有左子树或右子树的结点；**
3. **左右子树都有结点；**

对于1（要删除结点为叶子结点）直接删除，即直接解除父节点的引用即可，对于第2种情况（要删除的结点仅有一个儿子），只需用子结点替换掉父节点即可；而对于要删除的结点有两个儿子的情况，比较常用处理逻辑为，在其子树中找寻一个结点来替换，而这个结点我们成为中序后继结点。

### 代码实现

见`BinaryTree.java`