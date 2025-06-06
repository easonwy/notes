# 动态规划 (Dynamic Programming)

## 概述
动态规划是一种通过把原问题分解为相对简单的子问题的方式求解复杂问题的方法。它将子问题的结果存储起来，避免重复计算，从而提高算法的效率。

## 基本原理
1. 最优子结构
2. 重叠子问题
3. 状态转移方程
4. 边界条件

## 经典问题
1. 斐波那契数列
2. 最长公共子序列
3. 背包问题
4. 最短路径
5. 编辑距离

## 代码示例
### 斐波那契数列
```java
public class Fibonacci {
    public int fib(int n) {
        if (n <= 1) return n;
        
        int[] dp = new int[n + 1];
        dp[0] = 0;
        dp[1] = 1;
        
        for (int i = 2; i <= n; i++) {
            dp[i] = dp[i-1] + dp[i-2];
        }
        
        return dp[n];
    }
}
```

### 0-1背包问题
```java
public class Knapsack {
    public int knapsack(int W, int[] weights, int[] values, int n) {
        int[][] dp = new int[n + 1][W + 1];
        
        for (int i = 1; i <= n; i++) {
            for (int w = 1; w <= W; w++) {
                if (weights[i-1] <= w) {
                    dp[i][w] = Math.max(values[i-1] + dp[i-1][w-weights[i-1]], 
                                      dp[i-1][w]);
                } else {
                    dp[i][w] = dp[i-1][w];
                }
            }
        }
        
        return dp[n][W];
    }
}
```

## 解题步骤
1. 定义状态
2. 建立状态转移方程
3. 确定边界条件
4. 确定计算顺序
5. 空间优化（可选）

## 常见优化方法
1. 状态压缩
2. 滚动数组
3. 记忆化搜索
4. 二进制优化
5. 单调队列/栈优化

## 实际应用
1. 最短路径导航
2. 资源调度优化
3. 文字相似度比较
4. 视频编码压缩
5. 游戏AI决策

## 复杂度分析
1. 时间复杂度：通常为 O(n²) 或 O(n×m)
2. 空间复杂度：可以通过优化降至 O(n) 或 O(1)

## 进阶主题
1. 区间DP
2. 树形DP
3. 状态压缩DP
4. 数位DP
5. 概率DP

## 参考资料
1. [动态规划：从新手到专家](https://www.topcoder.com/community/competitive-programming/tutorials/dynamic-programming-from-novice-to-advanced/)
2. [算法导论 - 动态规划](https://mitpress.mit.edu/books/introduction-algorithms-fourth-edition)
3. [LeetCode - 动态规划题目集合](https://leetcode.com/tag/dynamic-programming/)