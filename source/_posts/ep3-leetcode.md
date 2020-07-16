---
title: ep3-leetcode
top: false
cover: false
toc: true
mathjax: true
date: 2020-07-11 18:35:40
password:
summary:
tags:
- leetcode
- 算法
- 剑指offer
categories:
- 编程算法
---
   摸了好久的鱼，开始逐渐恢复一下，熟悉一下java。  
  ## 题目 
  [二维数组中的查找](https://leetcode-cn.com/problems/er-wei-shu-zu-zhong-de-cha-zhao-lcof/)    


在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

 

示例:

现有矩阵 matrix 如下：
```
[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]

```
给定 target = 5，返回 true。

给定 target = 20，返回 false。

 

限制：

0 <= n <= 1000

0 <= m <= 1000



## 题解
### 我提交的代码
```
class Solution {
    public boolean findNumberIn2DArray(int[][] matrix, int target) {

        if(matrix == null || matrix.length ==0 ||matrix[0].length == 0){
            return false;
        }
        int m = matrix.length;
        int n = matrix[0].length;
        if(target < matrix[0][0] || target > matrix[n-1][m-1]){
            return false;
        }
        int y = 0;
        for (int i = 0,x = n-1; x >= 0 && i < m;){
            if(matrix[i][x] == target){
                return true;
            }
            else if(matrix[i][x] > target){  
                x--;
            }
            else{
                i++;
            }
        }
        return false;

    }
}
```
### 分析 
1. 提交的代码有编译错误，等待过一段时间后回来DEBUG。
2. 思路正确，把目标和右上角的元素比较大小，如果大于右上角元素，则行指针加一，小于右上角元素则指针减一。
   
### 他人解法
1. 官方题解

方法二：线性查找
由于给定的二维数组具备每行从左到右递增以及每列从上到下递增的特点，当访问到一个元素时，可以排除数组中的部分元素。

从二维数组的右上角开始查找。如果当前元素等于目标值，则返回 true。如果当前元素大于目标值，则移到左边一列。如果当前元素小于目标值，则移到下边一行。

可以证明这种方法不会错过目标值。如果当前元素大于目标值，说明当前元素的下边的所有元素都一定大于目标值，因此往下查找不可能找到目标值，往左查找可能找到目标值。如果当前元素小于目标值，说明当前元素的左边的所有元素都一定小于目标值，因此往左查找不可能找到目标值，往下查找可能找到目标值。

若数组为空，返回 false
初始化行下标为 0，列下标为二维数组的列数减 1
重复下列步骤，直到行下标或列下标超出边界
获得当前下标位置的元素 num
如果 num 和 target 相等，返回 true
如果 num 大于 target，列下标减 1
如果 num 小于 target，行下标加 1
循环体执行完毕仍未找到元素等于 target ，说明不存在这样的元素，返回 false`
```
Java

class Solution {
    public boolean findNumberIn2DArray(int[][] matrix, int target) {
        if (matrix == null || matrix.length == 0 || matrix[0].length == 0) {
            return false;
        }
        int rows = matrix.length, columns = matrix[0].length;
        int row = 0, column = columns - 1;
        while (row < rows && column >= 0) {
            int num = matrix[row][column];
            if (num == target) {
                return true;
            } else if (num > target) {
                column--;
            } else {
                row++;
            }
        }
        return false;
    }
}

```
复杂度分析

时间复杂度：O(n+m)O(n+m)。访问到的下标的行最多增加 n 次，列最多减少 m 次，因此循环体最多执行 n + m 次。
空间复杂度：O(1)O(1)。




2. 

  