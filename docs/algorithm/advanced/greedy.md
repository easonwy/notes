# 贪心算法 (Greedy Algorithm)

## 概述
贪心算法是一种在每一步选择中都采取当前状态下最好或最优的选择，从而希望导致结果是最好或最优的算法。

## 基本原理
1. 贪心选择性质
2. 最优子结构性质
3. 局部最优解
4. 全局最优解

## 经典问题
1. 活动选择问题
2. 背包问题（分数背包）
3. 霍夫曼编码
4. 最小生成树
5. 找零钱问题

## 代码示例
### 分数背包问题
```java
public class FractionalKnapsack {
    public double getMaxValue(int[] weights, int[] values, int capacity) {
        int n = weights.length;
        double[][] ratio = new double[n][2];
        
        // 计算性价比并存储原始索引
        for (int i = 0; i < n; i++) {
            ratio[i][0] = i;
            ratio[i][1] = (double) values[i] / weights[i];
        }
        
        // 按性价比降序排序
        Arrays.sort(ratio, (a, b) -> Double.compare(b[1], a[1]));
        
        double maxValue = 0;
        int currentWeight = 0;
        
        for (int i = 0; i < n; i++) {
            int idx = (int) ratio[i][0];
            if (currentWeight + weights[idx] <= capacity) {
                currentWeight += weights[idx];
                maxValue += values[idx];
            } else {
                double remain = (capacity - currentWeight);
                maxValue += values[idx] * (remain / weights[idx]);
                break;
            }
        }
        
        return maxValue;
    }
}
```

## 算法特点
### 优点
- 实现简单
- 执行效率高
- 适用于局部最优解就是全局最优解的问题

### 缺点
- 不一定能得到全局最优解
- 依赖于问题的贪心选择性质
- 难以证明算法的正确性

## 应用场景
1. 任务调度
2. 资源分配
3. 数据压缩
4. 网络路由
5. 负载均衡

## 常见问题类型
1. 选择问题
2. 分配问题
3. 装载问题
4. 交换问题
5. 覆盖问题

## 解题步骤
1. 将问题分解为若干个子问题
2. 找出适合的贪心策略
3. 求解每个子问题的局部最优解
4. 将局部最优解堆叠成全局解

## 实际应用
1. Dijkstra最短路径算法
2. Prim最小生成树算法
3. 哈夫曼编码
4. 集合覆盖问题
5. 作业调度问题

## 参考资料
1. [Introduction to Algorithms](https://mitpress.mit.edu/books/introduction-algorithms-fourth-edition)
2. [算法导论 - 贪心算法](https://www.bookstack.cn/read/algorithm-4th/spilt.4.algorithm-c5.md)
3. [Greedy Algorithms Tutorial](https://www.geeksforgeeks.org/greedy-algorithms/)