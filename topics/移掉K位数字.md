移掉K位数字
<a href="https://leetcode-cn.com/problems/remove-k-digits/submissions/" target="_blank"> leetcode-402 </a>
    
    给你一个以字符串表示的非负整数 num 和一个整数 k ，移除这个数中的 k 位数字，使得剩下的数字最小。请你以字符串形式返回这个最小的数字。
     
    示例 1 ：
    输入：num = "1432219", k = 3
    输出："1219"
    解释：移除掉三个数字 4, 3, 和 2 形成一个新的最小的数字 1219 。
    
    示例 2 ：
    输入：num = "10200", k = 1
    输出："200"
    解释：移掉首位的 1 剩下的数字为 200. 注意输出不能有任何前导零。
    
    示例 3 ：
    输入：num = "10", k = 2
    输出："0"
    解释：从原数字移除所有的数字，剩余为空就是 0 。
    
#### 思路
    维护一个单调递减栈，出栈最多不超过k次

```
func removeKdigits(num string, k int) string {
    if k >= len(num) {
        return "0"
    }
    stack := make([]byte, 0)
    for i := 0; i < len(num); i++ {
        //栈头比下一个大，出栈，且不超过k次
        for len(stack) > 0 && num[i] < stack[len(stack)-1] && k > 0 {
            stack = stack[:len(stack)-1]
            k--
        }
        stack = append(stack, num[i])
    }
    //k还大于0时，移除栈尾
    if k > 0 {
        stack = stack[:len(stack)-k]
    }
    i := 0
    //移除前缀0
    for ; i < len(stack); i++ {
        if stack[i] != '0' {
           break
        } 
    }
   
    res := string(stack[i:])
    //为空时，返回0
    if res == "" {
        return "0"
    }
    return res
}

```