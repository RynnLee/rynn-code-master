不同路径II
<a href="https://leetcode-cn.com/problems/unique-paths-ii/" target="_blank"> leetcode-63 </a>
    
    一个机器人位于一个 m x n 网格的左上角 （起始点在下图中标记为 “Start” ）。
    机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为 “Finish”）。
    现在考虑网格中有障碍物。那么从左上角到右下角将会有多少条不同的路径？
    网格中的障碍物和空位置分别用 1 和 0 来表示。
    
    示例 1：
    输入：obstacleGrid = [[0,0,0],[0,1,0],[0,0,0]]
    输出：2
    解释：3x3 网格的正中间有一个障碍物。
    从左上角到右下角一共有 2 条不同的路径：
    1. 向右 -> 向右 -> 向下 -> 向下
    2. 向下 -> 向下 -> 向右 -> 向右
    
    示例 2：
    输入：obstacleGrid = [[0,1],[0,0]]
    输出：1
    
    提示：
    m == obstacleGrid.length
    n == obstacleGrid[i].length
    1 <= m, n <= 100
    obstacleGrid[i][j] 为 0 或 1
    
#### 思路
    令dp[i][j]表示到达obstacleGrid[i][j]不同路径的条数
    当 obstacleGrid[i][j] = 1时，不可达，即dp[i][j] = 0
    dp[i][j] = dp[i-1][j] + dp[i][j-1]
```
func uniquePathsWithObstacles(obstacleGrid [][]int) int {
    if obstacleGrid == nil {
        return 0
    }
    if obstacleGrid[0][0] == 1 {
        return 0
    }
    dp := make([][]int, len(obstacleGrid))
    for i, _ := range dp {
        dp[i] = make([]int, len(obstacleGrid[0]))
    }
    dp[0][0] = 1
    for i := 0; i < len(obstacleGrid); i++ {
        for j := 0; j < len(obstacleGrid[0]); j++ {
            if i == 0 && j == 0 {
                continue;
            }
            //如果有障碍，dp[i][j]不可达
            if obstacleGrid[i][j] == 1 {
                dp[i][j] = 0
                continue
            }
            //i == 0 或者 j == 0,
            if i == 0 {
                dp[i][j] = dp[i][j-1] + 0
                continue
            }
            if j == 0 {
                dp[i][j] = dp[i-1][j] + 0
                continue
            }
             dp[i][j] = dp[i-1][j] + dp[i][j-1]
        }
    }
    return dp[len(dp)-1][len(dp[0])-1]
}
```