# LeetCode 第 1480 号问题：一维数组的动态和

**from zhanghanyuan**

题目来源于 LeetCode 上第 1480 号问题：一维数组的动态和。题目难度为 Easy，目前通过率相对较高 。

### 题目描述

给你一个数组 nums 。数组「动态和」的计算公式为：runningSum[i] = sum(nums[0]…nums[i]) 。

请返回 nums 的动态和。


**示例1:**

```
输入：nums = [1,2,3,4]
输出：[1,3,6,10]
解释：动态和计算过程为 [1, 1+2, 1+2+3, 1+2+3+4] 。
```

**示例1:**

```
输入：nums = [1,1,1,1,1]
输出：[1,2,3,4,5]
解释：动态和计算过程为 [1, 1+1, 1+1+1, 1+1+1+1, 1+1+1+1+1] 。
```
### 题目解析

动态规划，时间复杂度：O(n)

根据动态求和公式：temp[i] = temp[i-1] + nums[i];

如果采取暴力求接法，我们需要在在遍历到数组的每个元素的时候，从头开始求和直到这个位置的前一个元素。因此，我们采用动态规划的思想来设计：

每次遍历到一个新的位置，都将他与前面的所有和相加，有点类似迭代法的循环，每次这个前面的额元素也是我们想要的结果。

### 代码实现

```java
class Solution {
    public int[] runningSum(int[] nums) {
        int[] temp = new int [nums.length];
        temp[0] = nums[0];
        for (int i = 1;i < nums.length;i++){
            temp[i] = nums[i] + temp[i - 1];

        }
        return temp;
    }
}
```

### 结果描述

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：40.1 MB, 在所有 Java 提交中击败了17.51%的用户