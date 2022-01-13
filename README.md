//# KAHN-S-ALGORITHM
//TOPOLOGICAL SORTING OF A DIRECTED GRAPH USING BFS TRAVERSAL
#include<bits/stdc++.h>
using namespace std;
vector<int> toposort(int n,vector<int>adj[]){
    vector<int>in(n,0);
    for(int i=0;i<n;i++){
        for(auto it:adj[i]){
            in[it]++;
        }
    }
    queue<int>q;
    vector<int>topo;
    for(int i=0;i<n;i++){
        if(in[i]==0) q.push(i);
    }
    while(!q.empty()){
        int node=q.front();
        q.pop();
        topo.push_back(node);
        for(auto it:adj[node]){
            in[it]--;
            if(in[it]==0) q.push(it);
        }
    }
    return topo;
}
int main(){
    int t;
    cin>>t;
    while(t--){
        int n,m;
        cin>>n>>m;
        vector<int>adj[n];
        for(int i=0;i<m;i++){
            int u,v;
            cin>>u>>v;
            adj[u].push_back(v);
          //  adj[v].push_back(u);
        }
        vector<int>v=toposort(n,adj);
        for(auto i:v) cout<<i<<" ";
    }
}
