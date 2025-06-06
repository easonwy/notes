# 搜索算法 (Search Algorithms)

## 概述
搜索算法是一种在数据集中查找特定元素的算法。它们在计算机科学中扮演着重要角色，从简单的线性搜索到复杂的树形搜索都有广泛应用。

## 常见搜索算法
1. 线性搜索
2. 二分查找
3. 深度优先搜索(DFS)
4. 广度优先搜索(BFS)
5. 跳跃搜索
6. 插值搜索

## 代码示例
### 二分查找
```java
public class BinarySearch {
    public static int binarySearch(int[] arr, int target) {
        int left = 0;
        int right = arr.length - 1;
        
        while (left <= right) {
            int mid = left + (right - left) / 2;
            
            if (arr[mid] == target) {
                return mid;
            }
            
            if (arr[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        
        return -1;
    }
}
```

### 线性搜索
```java
public class LinearSearch {
    public static int linearSearch(int[] arr, int target) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == target) {
                return i;
            }
        }
        return -1;
    }
}
```

## 算法比较
| 算法 | 时间复杂度 | 空间复杂度 | 特点 |
|------|------------|------------|------|
| 线性搜索 | O(n) | O(1) | 简单，适用于小数据集 |
| 二分查找 | O(log n) | O(1) | 要求有序数组 |
| 跳跃搜索 | O(√n) | O(1) | 有序数组的折中方案 |
| DFS | O(V + E) | O(V) | 适用于图/树搜索 |
| BFS | O(V + E) | O(V) | 寻找最短路径 |

## 应用场景
1. 数据库查询
2. 文件系统搜索
3. 路径规划
4. 游戏AI
5. 推荐系统

## 优化策略
1. 索引构建
2. 哈希表使用
3. 二分搜索树
4. 平衡树优化
5. 缓存机制

## 实际应用
1. 数据库索引
2. 搜索引擎
3. 文本编辑器查找
4. GPS导航
5. 字典查找

## 参考资料
1. [Introduction to Algorithms](https://mitpress.mit.edu/books/introduction-algorithms-fourth-edition)
2. [算法导论 - 查找算法](https://www.bookstack.cn/read/algorithm-4th/spilt.2.algorithm-c3.md)
3. [GeeksforGeeks - Searching Algorithms](https://www.geeksforgeeks.org/searching-algorithms/)