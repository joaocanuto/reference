- [**Graphs**](#graphs)
  - [BFS](#bfs)
    - [Problemns](#problemns)

# Graphs

### BFS

```c
 #include <bits/stdc++.h>

using namespace std;

const int maxn = 1e5;

vector<int> edges[maxn];
int dist[maxn];

void bfs_basico(int source);

int main(){
	int N, M; cin >> N >> M;
	for(int i = 0; i < M; i++){
		int from, to; cin >> from >> to;
		edges[from].push_back(to);
		edges[to].push_back(from);
	}

	bfs_basico(1);

	cout << dist[N] << endl;
	return 0;
}

void bfs_basico(int source){
	queue<int> q;
	//nossa fila
	memset(dist, -1, sizeof dist);
	dist[source] = 0;
	q.push(source); // adicionando o primeiro na fila e declarando a distancia = 0

	while(q.size()){
		int frente = q.front();
		q.pop();

		for(int i = 0, fim = edges[frente].size(); i < fim; i++){
			int neigh = edges[frente][i];
			if(dist[neigh] == -1){
				dist[neigh] = dist[frente] + 1;
				q.push(neigh);
			}
		}
	}
}
```
##### Problemns
