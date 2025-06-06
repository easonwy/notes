# 排序算法 (Sorting Algorithms)

## 概述
排序算法是一种将一组数据按照特定顺序重新排列的算法。根据不同场景和需求，可以选择不同的排序算法来实现最优性能。

## 常见排序算法
1. 冒泡排序 (Bubble Sort)
2. 选择排序 (Selection Sort)
3. 插入排序 (Insertion Sort)
4. 快速排序 (Quick Sort)
5. 归并排序 (Merge Sort)
6. 堆排序 (Heap Sort)
7. 希尔排序 (Shell Sort)
8. 计数排序 (Counting Sort)

## 代码示例
### 快速排序
```java
public class QuickSort {
    public static void quickSort(int[] arr, int left, int right) {
        if (left < right) {
            int pivot = partition(arr, left, right);
            quickSort(arr, left, pivot - 1);
            quickSort(arr, pivot + 1, right);
        }
    }
    
    private static int partition(int[] arr, int left, int right) {
        int pivot = arr[right];
        int i = left - 1;
        
        for (int j = left; j < right; j++) {
            if (arr[j] <= pivot) {
                i++;
                swap(arr, i, j);
            }
        }
        
        swap(arr, i + 1, right);
        return i + 1;
    }
    
    private static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}
```

## 算法比较
| 算法 | 平均时间复杂度 | 最坏时间复杂度 | 空间复杂度 | 稳定性 |
|------|----------------|----------------|------------|--------|
| 冒泡排序 | O(n²) | O(n²) | O(1) | 稳定 |
| 选择排序 | O(n²) | O(n²) | O(1) | 不稳定 |
| 插入排序 | O(n²) | O(n²) | O(1) | 稳定 |
| 快速排序 | O(nlogn) | O(n²) | O(logn) | 不稳定 |
| 归并排序 | O(nlogn) | O(nlogn) | O(n) | 稳定 |
| 堆排序 | O(nlogn) | O(nlogn) | O(1) | 不稳定 |

## 选择策略
1. 数据规模小：插入排序
2. 数据基本有序：冒泡排序，插入排序
3. 数据规模大：快速排序，归并排序，堆排序
4. 要求稳定性：归并排序，冒泡排序
5. 空间要求严格：堆排序

## 优化技巧
1. 快速排序
   - 三数取中法选择基准
   - 随机选择基准
   - 处理重复元素
2. 归并排序
   - 小规模数据使用插入排序
   - 原地归并优化
3. 通用优化
   - 缓存优化
   - 并行化处理
   - 混合排序策略

## 实际应用
1. 数据库索引排序
2. 文件系统管理
3. 操作系统任务调度
4. 电商平台商品排序
5. 搜索引擎结果排序

## 参考资料
1. [排序算法可视化](https://visualgo.net/en/sorting)
2. [算法导论 - 排序算法](https://mitpress.mit.edu/books/introduction-algorithms-fourth-edition)
3. [GeeksforGeeks - Sorting Algorithms](https://www.geeksforgeeks.org/sorting-algorithms/)