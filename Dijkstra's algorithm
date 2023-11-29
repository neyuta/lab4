#include <iostream>
#include <limits.h>

#define V 9

using namespace std;

int minDistance(int dist[], bool sptSet[])
{
    int min = INT_MAX, min_index;
  
    for (int v = 0; v < V; v++)
        if (sptSet[v] == false && dist[v] <= min)
            min = dist[v], min_index = v;
  
    return min_index;
}

void printSolution(int parent[], int graph[V][V])
{
    cout << "Ребро \tВес\n";
    for (int i = 1; i < V; i++)
        cout << parent[i] << " - " << i << " \t" << graph[i][parent[i]] << "\n";
}

void dijkstra(int graph[V][V])
{
    int dist[V];
  
    bool sptSet[V];
  
    int parent[V];
  
    for (int i = 0; i < V; i++)
    {
        dist[i] = INT_MAX;
        sptSet[i] = false;
    }
  
    dist[0] = 0;
  
    parent[0] = -1;
  
    for (int count = 0; count < V-1; count++)
    {
        int u = minDistance(dist, sptSet);
  
        sptSet[u] = true;
  
        for (int v = 0; v < V; v++)
  
            if (!sptSet[v] && graph[u][v] && dist[u] + graph[u][v] < dist[v])
            {
                parent[v]  = u;
                dist[v] = dist[u] + graph[u][v];
            }
    }
  
    printSolution(parent, graph);
}

int main()
{
    int graph[V][V] = {{0, 3, 0, 0, 0, 0, 0, 10, 0},
                      {3, 0, 4, 5, 2, 0, 0, 0, 0},
                      {0, 4, 0, 6, 0, 0, 0, 0, 0},
                      {0, 5, 6, 0, 8, 0, 7, 0, 0},
                      {0, 2, 0, 8, 0, 5, 0, 9, 0},
                      {0, 0, 0, 0, 5, 0, 4, 8, 5},
                      {0, 0, 0, 7, 0, 4, 0, 0, 6},
                      {10, 0, 0, 0, 9, 8, 0, 0, 9},
                      {0, 0, 0, 0, 0, 5, 6, 9, 0}};
  
    dijkstra(graph);

    return 0;
}

