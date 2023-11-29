#include <iostream>
#include <vector>
#include <algorithm>
 
using namespace std;

struct Edge 
{
    int u, v, weight;
};

bool compareEdges(const Edge& a, const Edge& b) 
{
    return a.weight < b.weight;
}

int find(int parent[], int i) 
{
    if (parent[i] == -1)
        return i;
    return find(parent, parent[i]);
}

void unionSets(int parent[], int x, int y)
{
    int rootX = find(parent, x);
    int rootY = find(parent, y);
    parent[rootX] = rootY;
}

void primMST(vector<vector<int>>& graph, int V)
{
    vector<Edge> result;
    int* parent = new int[V];
    fill(parent, parent + V, -1);
 
    for (int count = 0; count < V - 1; ++count) 
    {
        Edge minEdge;
        minEdge.weight = INT_MAX;

        for (int u = 0; u < V; ++u) 
        {
            for (int v = 0; v < V; ++v)
            {
                if (graph[u][v] && find(parent, u) != find(parent, v) && graph[u][v] < minEdge.weight)
                {
                    minEdge.u = u;
                    minEdge.v = v;
                    minEdge.weight = graph[u][v];
                }
            }
        }
 
        result.push_back(minEdge);
        unionSets(parent, minEdge.u, minEdge.v);
    }
 
    cout << "Edges in the Minimum Spanning Tree:" << endl;
    cout << "| Edge | Weight |" << endl;
    cout << "|------|--------|" << endl;
 
    int totalWeight = 0;
    for (const auto& edge : result) 
    {
        cout << "| " << edge.u << " - " << edge.v << " | " << edge.weight << " |" << endl;
        totalWeight += edge.weight;
    }
 
    cout << "\nTotal Weight of the Minimum Spanning Tree: " << totalWeight << endl;
}
 
int main() 
{
    
    int V;
    cout << "Enter the number of vertices in the graph: ";
    cin >> V;
 
    vector<vector<int>> graph(V, vector<int>(V, 0));
    graph = { {0, 3, 2, 5, 0, 0, 0, 0},
            {3, 0, 0, 6, 7, 0, 0, 0},
            {2, 0, 0, 3, 0, 4, 0, 0},
            {5, 6, 3, 0, 0, 4, 5, 0},
            {0, 7, 0, 0, 0, 0, 8, 9},
            {0, 0, 4, 4, 0, 0, 6, 9},
            {0, 0, 0, 5, 8, 6, 0, 7},
            {0, 0, 0, 0, 9, 0, 7, 0} };
 
    primMST(graph, V);
 
    return 0;
}
