# 分治算法 (Divide and Conquer)

## 概述
分治算法是一种解决复杂问题的重要策略，通过将问题分解为更小的子问题，解决子问题后再将结果合并得到最终解决方案。

## 基本思想
1. 分解（Divide）：将原问题分解为若干个规模较小的子问题
2. 解决（Conquer）：递归地求解各个子问题
3. 合并（Combine）：将子问题的解组合成原问题的解

## 经典应用
1. 二分查找
2. 归并排序
3. 快速排序
4. 大整数乘法
5. 矩阵乘法（Strassen算法）
6. 最近点对问题

## 代码示例
### 归并排序
```java
public static void mergeSort(int[] arr, int left, int right) {
    if (left < right) {
        int mid = (left + right) / 2;
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);
        merge(arr, left, mid, right);
    }
}
```

### 快速排序
```java
public static void quickSort(int[] arr, int left, int right) {
    if (left < right) {
        int pivot = partition(arr, left, right);
        quickSort(arr, left, pivot - 1);
        quickSort(arr, pivot + 1, right);
    }
}
```

## 算法分析
1. 时间复杂度
   - 最优情况：O(nlogn)
   - 最坏情况：O(n²)
2. 空间复杂度：O(logn)

## 优缺点
### 优点
- 将复杂问题简化为简单问题
- 具有良好的可并行性
- 适合解决规模较大的问题

### 缺点
- 递归调用可能带来较大的开销
- 对某些问题可能产生重复计算

## 应用场景
1. 排序算法
2. 搜索算法
3. 图形处理
4. 数值计算
5. 数据压缩

## 参考资料
1. [Introduction to Algorithms](https://mitpress.mit.edu/books/introduction-algorithms-fourth-edition)
2. [算法导论 - 分治策略](https://www.bookstack.cn/read/algorithm-4th/spilt.3.algorithm-c4.md)
3. [GeeksforGeeks - Divide and Conquer](https://www.geeksforgeeks.org/divide-and-conquer/)