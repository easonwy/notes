# 图论算法 (Graph Algorithms)

## 概述
图论算法是一系列用于解决图结构相关问题的算法，包括图的遍历、最短路径、最小生成树等。这些算法在网络分析、路由规划、社交网络等领域有广泛应用。

## 基本概念
1. 图的表示
   - 邻接矩阵
   - 邻接表
2. 图的类型
   - 有向图/无向图
   - 加权图/无权图
   - 连通图/非连通图
3. 基本术语
   - 顶点(Vertex)
   - 边(Edge)
   - 路径(Path)
   - 环(Cycle)

## 常见算法
### 图的遍历
1. 深度优先搜索(DFS)
2. 广度优先搜索(BFS)

### 最短路径
1. Dijkstra算法
2. Floyd算法
3. Bellman-Ford算法

### 最小生成树
1. Prim算法
2. Kruskal算法

## 代码示例
### DFS实现
```java
public class Graph {
    private int V;
    private List<List<Integer>> adj;
    
    public void DFS(int v, boolean[] visited) {
        visited[v] = true;
        System.out.print(v + " ");
        
        for (int n : adj.get(v)) {
            if (!visited[n]) {
                DFS(n, visited);
            }
        }
    }
}
```

### Dijkstra算法实现
```java
public class Dijkstra {
    public int[] shortestPath(int[][] graph, int start) {
        int n = graph.length;
        int[] dist = new int[n];
        boolean[] visited = new boolean[n];
        
        Arrays.fill(dist, Integer.MAX_VALUE);
        dist[start] = 0;
        
        for (int i = 0; i < n-1; i++) {
            int u = minDistance(dist, visited);
            visited[u] = true;
            
            for (int v = 0; v < n; v++) {
                if (!visited[v] && graph[u][v] != 0 && 
                    dist[u] != Integer.MAX_VALUE &&
                    dist[u] + graph[u][v] < dist[v]) {
                    dist[v] = dist[u] + graph[u][v];
                }
            }
        }
        return dist;
    }
}
```

## 应用场景
1. 社交网络分析
2. 地图导航系统
3. 网络路由规划
4. 任务调度系统
5. 依赖关系分析

## 复杂度分析
| 算法 | 时间复杂度 | 空间复杂度 |
|------|------------|------------|
| DFS | O(V + E) | O(V) |
| BFS | O(V + E) | O(V) |
| Dijkstra | O(V²) | O(V) |
| Floyd | O(V³) | O(V²) |
| Prim | O(V²) | O(V) |
| Kruskal | O(E log E) | O(V) |

## 进阶主题
1. 强连通分量
2. 拓扑排序
3. 欧拉回路
4. 哈密顿回路
5. 网络流算法

## 优化技巧
1. 邻接表代替邻接矩阵
2. 优先队列优化Dijkstra
3. 并查集优化Kruskal
4. 二分图判定
5. 环检测优化

## 参考资料
1. [Introduction to Algorithms](https://mitpress.mit.edu/books/introduction-algorithms-fourth-edition)
2. [算法导论 - 图论](https://www.bookstack.cn/read/algorithm-4th/spilt.5.algorithm-c6.md)
3. [Graph Theory Tutorials](https://www.geeksforgeeks.org/graph-data-structure-and-algorithms/)