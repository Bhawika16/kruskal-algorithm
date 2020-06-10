#include <iostream>
#include <algorithm>
using namespace std;

class Edges
{
public:
	int source;
	int dest;
	int weight; 
	
};

bool compare(Edges e1,Edges e2){
	return e1.weight < e2.weight;
}

int findParent(int v,int parent[]){
	if(parent[v] == v)
		return v;
	return findParent(parent[v],parent);
}

int main(){
	int V;
	cin>>V; //No. of vertices
	int n;
	cin>>n; //No. of Edges
	int src,dst,wt;
	Edges E[n];
	for (int i = 0; i < n; ++i){
		cin>>src;
		cin>>dst;
		cin>>wt;
		E[i].source = src;
		E[i].dest = dst;
		E[i].weight = wt;  
	}

	sort(E,E+n,compare);
	// Sort Edges based on their weights

	int parent[V];
	for (int i = 0; i < V; ++i)	{
		parent[i] = i;
	}

	int i=0;
	int count=0;
	Edges currentEdge[V-1]; // Stores MST 

	while(count<V-1){ // Runs till V-1 times
		 
		 int sourceParent = findParent(E[i].source,parent);
		 int destParent = findParent(E[i].dest,parent);

		 if(sourceParent != destParent){ // checks if no cycle
		 	currentEdge[count].source = E[i].source;
		 	currentEdge[count].dest = E[i].dest;
		 	currentEdge[count].weight = E[i].weight;
		 	count++;
		 	parent[sourceParent] = E[i].dest;	
		 }

		 i++;
	}
	cout<<"\nMinimum spanning Tree:\n";
	for (int i = 0; i < V-1; ++i){
		cout<<currentEdge[i].source<<" "<<currentEdge[i].dest<<" ";
		cout<<currentEdge[i].weight<<endl;
	}
	return 0;

}
