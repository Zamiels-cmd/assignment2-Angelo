# assignment2-Angelo
# David Angelo
## Likes food from Subway

It's right next to town square **Eat Fresh**

---
## List
From NW Missouri Regional Airport
1. Head southwest on Hawk Rd toward MO-46 E
2. Turn left onto MO-46 E
3. Turn left onto N Buchanan St
4. Turn right onto W 6th St

What to get
* Italian BMT
* Spicy Italian
* A sandwich
* Chips
* Cookies
* Water

[More about me](AboutMe.md)
___
## Tables

Activities

|Activity|location|cost|
|---|---|---|
|Math|Anywhere|$0|
|Reading|Anywhere|$0|
|Eating Subway|Subway|$5-$20|
|Walking|Anywhere|$0|

---
## Pithy Quotes
>All first order linear differiential equations are solvable.\
>However, the first statement doesn't define solvable.\
*David Angelo*

---
## Code Fencing
### Minimum spanning tree - Kruskal with Disjoint Set Union
>1. Sort all the edges in non-decreasing order of their weight. 
>2. Pick the smallest edge. Check if it forms a cycle with the spanning tree formed so far. If cycle is not formed, include this edge. Else, discard it. 
>3. Repeat step#2 until there are (V-1) edges in the spanning tree.\
[Kruskal's Algorithm](https://www.geeksforgeeks.org/kruskals-minimum-spanning-tree-algorithm-greedy-algo-2/)

```
vector<int> parent, rank;

void make_set(int v) {
    parent[v] = v;
    rank[v] = 0;
}

int find_set(int v) {
    if (v == parent[v])
        return v;
    return parent[v] = find_set(parent[v]);
}

void union_sets(int a, int b) {
    a = find_set(a);
    b = find_set(b);
    if (a != b) {
        if (rank[a] < rank[b])
            swap(a, b);
        parent[b] = a;
        if (rank[a] == rank[b])
            rank[a]++;
    }
}

struct Edge {
    int u, v, weight;
    bool operator<(Edge const& other) {
        return weight < other.weight;
    }
};

int n;
vector<Edge> edges;

int cost = 0;
vector<Edge> result;
parent.resize(n);
rank.resize(n);
for (int i = 0; i < n; i++)
    make_set(i);

sort(edges.begin(), edges.end());

for (Edge e : edges) {
    if (find_set(e.u) != find_set(e.v)) {
        cost += e.weight;
        result.push_back(e);
        union_sets(e.u, e.v);
    }
}
```
[Kruskal's Algorithm in Code](https://cp-algorithms.com/graph/mst_kruskal_with_dsu.html)
