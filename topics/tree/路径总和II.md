路径总和II
   <a href="https://leetcode-cn.com/problems/path-sum-ii/" target="_blank"> leetcode-113 </a>
   
          给你二叉树的根节点 root 和一个整数目标和 targetSum ，找出所有 从根节点到叶子节点 路径总和等于给定目标和的路径。
          叶子节点 是指没有子节点的节点。
          
          示例 1：
          输入：root = [5,4,8,11,null,13,4,7,2,null,null,5,1], targetSum = 22
          输出：[[5,4,11,2],[5,8,4,5]]
          
          示例 2：
          输入：root = [1,2,3], targetSum = 5
          输出：[]
       
   ## 思路
       递归定义dfs(node, targetSum)
       dfs(node, targetSum) = (node.Left, targetSum-node.Val) U (node.Right, targetSum-node.Val)
   ```
   func pathSum(root *TreeNode, targetSum int) [][] int {
       //保存遍历路径
       var path []int
       var r [][]int
       var dfs func(root *TreeNode, targetSum int)
       dfs = func(root *TreeNode, targetSum int) {
           if  root == nil {
               return
           }
           path = append(path, root.Val)
           //下一次目标值减去val
           targetSum -= root.Val
           //fmt.Println("path", path, "target", targetSum)
           if root.Left == nil && root.Right == nil && targetSum == 0 {
               //叶节点时，保存path路径
               r = append(r, append([]int{}, path...))
               return
           }
           //递归左节点
           dfs(root.Left, targetSum)
           if root.Left != nil {
               //节点不为空，path需要将节点val入栈，这里回溯调，需要出栈
               path = path[:len(path)-1]
           }
           dfs(root.Right, targetSum)
           if root.Right != nil {
               //节点不为空，path需要将节点val入栈，这里回溯调，需要出栈
               path = path[:len(path)-1]
           }
       }
       dfs(root, targetSum)
       return r
   }
   ```