计算24点

    还记得小时候计算24点的小游戏吗，4张牌，没张只能使用一次，加减乘除得到24


#### 思路
    4张牌中任意2张，加减乘除得到一个数；那么现在就有3个数，依次类推，直到只剩1个数，判断这个数是否是24点

```
// 计算24点
func count24(slc [4]int) []string {
	var result = make([]string, 0)
	// numStrs 用来存储计算过程的算术表达式
	var f24 func(nums []int, numStrs []string)
	// 计算24点
	// 1、任取nums中的2个数
	// 2、加减乘除得到新的数
	// 3、将新的数和nums中的其他数做为新的输入
	// 4、重复1、2、3，直到nums中只有1个数，当此数为24时，表示得到一条解
	f24 = func(nums []int, numStrs []string) {
		if len(nums) == 1 {
			if nums[0] == 24 {
				// fmt.Println(nums[0], numStrs[0])
				// 记录算术表达式
				result = append(result, numStrs[0])
			}
			return
		}
		for i := 0; i < len(nums); i++ {
			for j := i + 1; j < len(nums); j++ {
				tmpSlc := make([]int, 0, len(nums)-1)
				tmpStrSlc := make([]string, 0, len(nums)-1)
				tmpStr := ""
				for k := 0; k < len(nums); k++ {
					if k == i || k == j {
						continue
					}
					tmpSlc = append(tmpSlc, nums[k])
					tmpStrSlc = append(tmpStrSlc, numStrs[k])
				}
				tmpSlc = append(tmpSlc, nums[i]+nums[j])
				tmpStr = fmt.Sprintf("(%s+%s)", numStrs[i], numStrs[j])
				tmpStrSlc = append(tmpStrSlc, tmpStr)
				f24(tmpSlc, tmpStrSlc)
				// 回朔
				tmpSlc = tmpSlc[:len(tmpSlc)-1]
				tmpStrSlc = tmpStrSlc[:len(tmpStrSlc)-1]

				tmpSlc = append(tmpSlc, nums[i]-nums[j])
				tmpStr = fmt.Sprintf("(%s-%s)", numStrs[i], numStrs[j])
				tmpStrSlc = append(tmpStrSlc, tmpStr)
				f24(tmpSlc, tmpStrSlc)
				tmpSlc = tmpSlc[:len(tmpSlc)-1]
				tmpStrSlc = tmpStrSlc[:len(tmpStrSlc)-1]

				tmpSlc = append(tmpSlc, nums[i]*nums[j])
				tmpStr = fmt.Sprintf("%s*%s", numStrs[i], numStrs[j])
				tmpStrSlc = append(tmpStrSlc, tmpStr)
				f24(tmpSlc, tmpStrSlc)
				tmpSlc = tmpSlc[:len(tmpSlc)-1]
				tmpStrSlc = tmpStrSlc[:len(tmpStrSlc)-1]

				if nums[j] != 0 {
					tmpSlc = append(tmpSlc, nums[i]/nums[j])
					tmpStr = fmt.Sprintf("%s/%s", numStrs[i], numStrs[j])
					tmpStrSlc = append(tmpStrSlc, tmpStr)
					f24(tmpSlc, tmpStrSlc)
					tmpSlc = tmpSlc[:len(tmpSlc)-1]
					tmpStrSlc = tmpStrSlc[:len(tmpStrSlc)-1]
				}

				tmpSlc = append(tmpSlc, nums[j]-nums[i])
				tmpStr = fmt.Sprintf("(%s-%s)", numStrs[j], numStrs[i])
				tmpStrSlc = append(tmpStrSlc, tmpStr)
				f24(tmpSlc, tmpStrSlc)
				tmpSlc = tmpSlc[:len(tmpSlc)-1]
				tmpStrSlc = tmpStrSlc[:len(tmpStrSlc)-1]

				if nums[i] != 0 {
					tmpSlc = append(tmpSlc, nums[j]/nums[i])
					tmpStr = fmt.Sprintf("%s/%s", numStrs[j], numStrs[i])
					tmpStrSlc = append(tmpStrSlc, tmpStr)
					f24(tmpSlc, tmpStrSlc)
					tmpSlc = tmpSlc[:len(tmpSlc)-1]
					tmpStrSlc = tmpStrSlc[:len(tmpStrSlc)-1]
				}
			}
		}
	}
	var (
		nums    = make([]int, 0, len(slc))
		numStrs = make([]string, 0, len(slc))
	)
	for _, v := range slc {
		nums = append(nums, v)
		numStrs = append(numStrs, strconv.Itoa(v))
	}
	f24(nums, numStrs)
	fmt.Println(result)
	return result
}
```