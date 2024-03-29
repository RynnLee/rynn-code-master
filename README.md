
**珍惜现在写代码的时间**

**本项目是对以前编程训练的一些梳理和总结**

## 算法的复杂度
* 算法注重 *最坏情况下*的*最优解*，而非平均情况或最好情况。
* 大O表示法 

    这张图很重要，复杂度高一个级别差别是天壤之别。
    O(logN) 和 O(1)是如此接近。
    
    <img width="45%" height="30%" src="https://github.com/RynnLee/rynn-code-master/blob/master/pics/big-o.png"/>

## 线性表 - 双指针
 通常能控制时间在O(n)，通常用于子串问题、极值问题。
 核心点是理清前后指针移动相关逻辑。
 * [二分查找](./topics/二分查找.md) 
 * [盛水最多的容器](./topics/盛水最多的容器.md) 
 * [最长无重复子串](./topics/最长无重复子串.md) 
 * [最小覆盖子串](./topics/最小覆盖子串.md) 
 
## 线性表 - 单调栈
 * [最小栈](./topics/最小栈.md)
 * [去除重复字母](./topics/去除重复字母.md)
 * [每日温度](./topics/每日温度.md)
 * [移掉K位数字](./topics/移掉K位数字.md)
 
 ## 动态规划
    动态规划的核心是寻找状态迁移方程
    当问题当规模+1，寻找f(n+1)和f(n)之间当关系
 * [入门问题-爬楼梯](topics/dp/爬楼梯.md)
 * [最小路径和](./topics/dp/最小路径和.md)
 * [不同路径II](./topics/dp/不同路径II.md)
 * [最长回文子串](./topics/dp/最长回文子串.md)
 * [零钱兑换](./topics/dp/零钱兑换.md)
 
 
 ## 回溯&剪枝
    一般通过dfs搜索
    通常回溯能优化保存路径消耗的空间
    剪枝能提前终止搜索，降低时间消耗
 * [全排列](./topics/全排列.md)
 * [组合总和](./topics/组合总和.md)
 * [k个数的组合](./topics/k个数的组合.md)
 
## [树](./pics/tree-type.png)
二叉树遍历

 * [先序非递归](./topics/tree/先序非递归.md)
 * [中序非递归](./topics/tree/中序非递归.md) 
 * [后序非递归](./topics/tree/后序非递归.md) 
 * [层序遍历](./topics/tree/二叉树的层序遍历.md)
 
 树的其他问题
    
    树的其他问题通常用到递归，递归方法的参数和方法定义是思路的关键。
 * [路径总和II](topics/tree/路径总和II.md)
 * [求根节点到叶节点数字之和](topics/tree/根节点到叶节点数字之和.md)
 * [最大路径和](topics/tree/最大路径和.md)
 

  DFS搜索
  * [岛屿数量](topics/岛屿数量.md)
  * [子集](topics/子集.md)
  * [获取目录文件](topics/获取目录文件.md)
  
## 其他
  * [计算24点](topics/count24.md)
