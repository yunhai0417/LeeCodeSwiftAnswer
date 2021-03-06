# LeeCodeSwiftAnswer - 两数之和 -1
>难度：简单

###题目描述
给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。
你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍。

**示例:**
```
给定 nums = [2, 7, 11, 15], target = 9
因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```


###一遍哈希表
> 在进行迭代并将元素插入到表中的同时，我们还会回过头来检查表中是否已经存在当前元素所对应的目标元素。如果它存在，那我们已经找到了对应解，并立即将其返回。

```
func twoSum(_ nums: [Int], _ target: Int) -> [Int] {
        var result = [Int]()
        var dic = [Int:Int]()
        var findex = 0
        for index in nums {
            let needKey = target - index 
            if let lastIndex = dic[needKey] {
                result.append(lastIndex)
                result.append(findex)
                return result
            } 
            dic[index] = findex
            findex += 1
        }
        return result
    }
```