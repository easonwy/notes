# 回溯算法 (Backtracking)

## 概述
回溯算法是一种通过探索所有可能的候选解来找出所有解的算法。若候选解被确认不是解，回溯算法会舍弃该解，回溯到上一步，继续尝试其他候选解。

## 基本思想
1. 确定问题的解空间
2. 确定约束条件
3. 搜索解空间（深度优先）
4. 剪枝优化

## 经典问题
1. N皇后问题
2. 数独求解
3. 全排列问题
4. 子集问题
5. 组合总和

## 代码示例
### N皇后问题
```java
public class NQueens {
    public List<List<String>> solveNQueens(int n) {
        List<List<String>> solutions = new ArrayList<>();
        int[] queens = new int[n];
        Arrays.fill(queens, -1);
        solve(solutions, queens, 0, n);
        return solutions;
    }
    
    private void solve(List<List<String>> solutions, int[] queens, int row, int n) {
        if (row == n) {
            solutions.add(generateBoard(queens, n));
            return;
        }
        
        for (int col = 0; col < n; col++) {
            if (isValid(queens, row, col)) {
                queens[row] = col;
                solve(solutions, queens, row + 1, n);
                queens[row] = -1;
            }
        }
    }
}
```

## 算法特点
### 优点
- 可以找到所有可能的解
- 实现简单，容易理解
- 适用于组合优化问题

### 缺点
- 时间复杂度可能很高
- 解空间可能很大
- 不适合解决规模较大的问题

## 应用场景
1. 路径寻找问题
2. 图的着色问题
3. 迷宫求解
4. 八皇后问题
5. 数独游戏求解

## 优化策略
1. 合理剪枝
2. 提前判断无效分支
3. 优化状态表示
4. 记忆化搜索
5. 启发式搜索

## 实战应用
1. 迷宫寻路算法
2. 游戏AI决策树
3. 约束满足问题
4. 组合优化问题

## 参考资料
1. [Introduction to Algorithms](https://mitpress.mit.edu/books/introduction-algorithms-fourth-edition)
2. [算法导论 - 回溯法](https://www.bookstack.cn/read/algorithm-4th/spilt.3.algorithm-c4.md)
3. [LeetCode - Backtracking](https://leetcode.com/tag/backtracking/)