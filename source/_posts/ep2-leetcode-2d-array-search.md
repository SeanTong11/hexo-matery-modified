---
title: ep2 leetcode 2d_array_search
top: false
cover: false
toc: true
mathjax: true
date: 2020-06-12 16:19:24
password:
summary:
tags:
- leetcode
- 算法
- 剑指offer
categories:
- 编程算法
---
   这是我的第一篇leetcode文章，计划先刷刷剑指offer，熟悉一下基本套路，掌握一些高频内容。  
  ## 题目 
  [数组中重复的数字](https://leetcode-cn.com/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/)    

找出数组中重复的数字。 

在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

示例 1：

输入：
[2, 3, 1, 0, 2, 5, 3]
输出：2 或 3 
 

限制：

2 <= n <= 100000

## 题解
### 我提交的代码
```
class Solution {
    public int findRepeatNumber(int[] nums) {
        int n = nums.length;
        int[] arr = new int[n+1];
        Arrays.fill(arr, 0);
        for(int x = 0; x < n; x++ ){
            if(arr[nums[x]]!=0){
                return nums[x];
            }
            else{
                arr[nums[x]]++;
            }
        }
        return -1;
    }
}
```
### 思路 
1. 可以先将数组排序，前一个和后一个对比。
2. 使用数组或hashset做哈希表。  
   
### 他人解法
1. 使用hashset
~~~
class Solution {
    public int findRepeatNumber(int[] nums) {
        Set<Integer> set = new HashSet<Integer>();
        int repeat = -1;
        for (int num : nums) {
            if (!set.add(num)) {
                repeat = num;
                break;
            }
        }
        return repeat;
    }
}
~~~
2. 原地交换时间复杂度为O(n),空间复杂度为常数
~~~
class Solution {
    public int findRepeatNumber(int[] nums) {
        int i = 0;
        while(i < nums.length) {
            if(nums[i] == i) {
                i++;
                continue;
            }
            if(nums[nums[i]] == nums[i]) return nums[i];
            int tmp = nums[i];
            nums[i] = nums[tmp];
            nums[tmp] = tmp;
        }
        return -1;
    }
}
~~~
作者：jyd  
链接：https://leetcode-cn.com/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/solution/mian-shi-ti-03-shu-zu-zhong-zhong-fu-de-shu-zi-yua/


  
