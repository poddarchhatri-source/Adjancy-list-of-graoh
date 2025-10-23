# Adjancy-list-of graph
Graph Representation using Adjacency List in C++
#include<iostream>
#include<list>
#include<vector>
#include <utility>
using namespace std;
vector<list<pair<int,int>>> graph;
void add_edge(int src, int dest, int w = 0, bool directed = true) {
    graph[src].push_back({dest, w});
    if (!directed) {
        graph[dest].push_back({src, w});
    }
}
void display(){
    cout<<"Display the graph";
    for(int i=0;i<graph.size();i++){
        cout<<i<<" ->";
        for(auto el: graph[i]){
            cout<<"( "<<el.first<<","<<el.second<<" )";
        }
        cout<<endl;
    }

}
int main() {
    cout << "Enter the no of vertex and edges:";
    int v, e;
    cin >> v >> e;
    cout << "is graph is directed if yes enter 1 ,if no enter 0: ";
    bool isDirected;
    cin >> isDirected;
    cout << "is graph is weighted graph if yes enter 1 ,if no enter 0: ";
    bool isWeighted;
    cin >> isWeighted;
    graph.resize(v, list<pair<int, int>>());
    if (isDirected) { // graph is directed
        if (isWeighted) { // weighted graph
            while (e--) {
                int src, dest, wt;
                cin >> src >> dest >> wt;
                add_edge(src, dest, wt, true);
            }
        } else { // unweighted graph
            while (e--) {
                int src, dest;
                cin >> src >> dest;
                add_edge(src, dest, 0, true);
            }
        }
    } else { // graph is undirected
        if (isWeighted) { // weighted graph
            while (e--) {
                int src, dest, wt;
                cin >> src >> dest >> wt;
                add_edge(src, dest, wt, false);
            }
        } else { // unweighted graph
            while (e--) {
                int src, dest;
                cin >> src >> dest;
                add_edge(src, dest, 0, false);
            }
        }
    }
    display();
}
