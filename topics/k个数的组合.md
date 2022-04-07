k个数的组合
<a href="https://leetcode-cn.com/problems/combinations/" target="_blank"> leetcode-77 </a>
    
    给定两个整数 n 和 k，返回范围 [1, n] 中所有可能的 k 个数的组合。
    你可以按 任何顺序 返回答案。
    
    示例 1：
    输入：n = 4, k = 2
    输出：
    [
      [2,4],
      [3,4],
      [2,3],
      [1,2],
      [1,3],
      [1,4],
    ]
    
    示例 2：
    输入：n = 1, k = 1
    输出：[[1]]
     
#### 思路
    定义dfs = func(start, n, k int) 表示从start 到 n，选k个数的组合
    当选中start时，dfs(start+1, n, k-1)
    当不选中start时， ，dfs(start+1, n, k)
    k = 0时，保存path
```
func combine(n int, k int) (r [][]int) {
    //存储path
    path := make([]int, 0)
    var dfs func(start, k int)
    //从start到n，选择k个数的组合
    dfs = func(start, k int) {
        //k为0时，保存path
        if k == 0 {
            r = append(r, append([]int{}, path...))
            return
        }
        //约束k达到减枝效果. start边界判定
        if start < 1 || start > n || k < 0 {
            return
        }
        //保存start
        path = append(path, start)
        //递归，start+1 到 n,取k-1个数的组合
        dfs(start+1, k - 1)
        //回溯path
        path = path[:len(path)-1]
        //start不取，从start+1 到 n,取k个数的组合
        dfs(start+1, k)
    }
    dfs(1, k)
    return r
}
```