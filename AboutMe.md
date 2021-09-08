# BHUVAN CHANDRA SARAKAM

I love Pop Songs of Hollywood, Bollywood and Tollywood. I try playing guitar for relaxing and ride One Wheel Pint for Stunt fun. I aspire to be a great coder and a great writer to NETFLIX oneday.

![MyPic](images/Bhuvan_Pic2.jpg)

---
###### My Favourite Food/Drinks
| Foods/Drink | Location | Cost |
| --- | --- | ---: |
| Chicken Pulav | Raju gari dhaba | 90 |
| Veg Fried Rice | Dolphin Restaurant | 50 |
| Chicken Biryani | Coastal Dhaba | 110 |
| Appollo Fish | Vihar | 165 |

---
###### My Favourite Quotes

> "When you sit with a nice girl for two hours you think it's only a minute, but when you sit on a hot stove for a minute you think it's two hours. That's relativity."
>                                                   *-Albert Einstein*
>
>"The Greatness of a person has to be estimated by his ability to tolerate provoking situations."
>                                                   *-Radhanath Swami*


---
###### Edmonds-Karp algorithm

>The idea of Edmonds-Karp is to use BFS in Ford Fulkerson implementation as BFS always picks a path with minimum number of edges. When BFS is used, the worst case time complexity can be reduced to O(VE2).

Lets go to GeeksforGeeks <https://www.geeksforgeeks.org/ford-fulkerson-algorithm-for-maximum-flow-problem/>

```
int n;
vector<vector<int>> capacity;
vector<vector<int>> adj;

int bfs(int s, int t, vector<int>& parent) {
    fill(parent.begin(), parent.end(), -1);
    parent[s] = -2;
    queue<pair<int, int>> q;
    q.push({s, INF});

    while (!q.empty()) {
        int cur = q.front().first;
        int flow = q.front().second;
        q.pop();

        for (int next : adj[cur]) {
            if (parent[next] == -1 && capacity[cur][next]) {
                parent[next] = cur;
                int new_flow = min(flow, capacity[cur][next]);
                if (next == t)
                    return new_flow;
                q.push({next, new_flow});
            }
        }
    }

    return 0;
}

int maxflow(int s, int t) {
    int flow = 0;
    vector<int> parent(n);
    int new_flow;

    while (new_flow = bfs(s, t, parent)) {
        flow += new_flow;
        int cur = t;
        while (cur != s) {
            int prev = parent[cur];
            capacity[prev][cur] -= new_flow;
            capacity[cur][prev] += new_flow;
            cur = prev;
        }
    }

    return flow;
}
```
Lets go to CP Algorithm page <https://cp-algorithms.com/graph/edmonds_karp.html>
