# assignment2-alaparthi
# teja
##### hyderabad

>Hyderabad is the capital of southern India's Telangana state. A major center for the technology industry, it's home to many upscale restaurants and shops.
>Its historic sites include Golconda Fort, a former diamond-trading center that was once the Qutb Shahi dynastic capital.**The Charminar** a 16th-century mosque whose 4 arches support towering minarets, is an old city landmark near the long-standing Laad Bazaar.Hyderabad is the capital and largest city of the South Indian state of Telangana. It was ruled by the **Qutub Shahis, Mughals and the Nizams** which shaped its history.

----
# Heading for access to reach the place with order list and unordered list
1. start from maryville.
  1. go to kansas airport.
  2. go to chicago airport.
  3. go to delhi airport.
  4. from delhi to hyderabad Airport
2. route map to charminar
    1. hyderabad Airport to metro station
    2. Jubilee Bus Station
    3. Aramghar Cross Road
    4. Koti Nayapul
    5. Charminar
* Items to carry
  * camera
  * currency
  * Id proofs
  * credit and debit cards

**[link to about me](AboutMe.md)**

------
# Heading for the  creating a Table foods and drinks

*Introduction:*
 The following is to create a table with atleast 4 food/drinks that you would recommend someone try. Include a short paragraph that introduces the table.

|Mandatory   |fav1            |fav2             |fav3             |fav4            |
|:--------:  |:---------:     |:---------:      |:----------:     |:----------:    |
|Food        |biryani         |idly             |chicken fry      |Coke            |
|Location    |Hyderabad       |guntur           |Home             |Any             |
|Amount      |600             |60               |300              |100             |

-----
# Section of Quotes
>"Success is not final; failure is not fatal: It is the courage to continue that counts."
>*Author:* Winston S. Churchill<br>
>"Success usually comes to those who are too busy to be looking for it."
>*Author:* Henry David Thoreau

-----
# create a new section using code fencing
>In graph theory, a cycle in a graph is a non-empty trail in which the only repeated vertices are the first and last vertices. A directed cycle in a directed graph is a non-empty directed trail in which the only repeated vertices are the first and last vertices.

A graph without cycles is called an acyclic graph. A directed graph without directed cycles is called a directed acyclic graph. A connected graph without cycles is called a tree.<https://en.wikipedia.org/wiki/Cycle_(graph_theory)>
```
int n;
vector<vector<int>> adj;
vector<char> color;
vector<int> parent;
int cycle_start, cycle_end;

bool dfs(int v) {
    color[v] = 1;
    for (int u : adj[v]) {
        if (color[u] == 0) {
            parent[u] = v;
            if (dfs(u))
                return true;
        } else if (color[u] == 1) {
            cycle_end = v;
            cycle_start = u;
            return true;
        }
    }
    color[v] = 2;
    return false;
}

void find_cycle() {
    color.assign(n, 0);
    parent.assign(n, -1);
    cycle_start = -1;

    for (int v = 0; v < n; v++) {
        if (color[v] == 0 && dfs(v))
            break;
    }

    if (cycle_start == -1) {
        cout << "Acyclic" << endl;
    } else {
        vector<int> cycle;
        cycle.push_back(cycle_start);
        for (int v = cycle_end; v != cycle_start; v = parent[v])
            cycle.push_back(v);
        cycle.push_back(cycle_start);
        reverse(cycle.begin(), cycle.end());

        cout << "Cycle found: ";
        for (int v : cycle)
            cout << v << " ";
        cout << endl;
    }
}

int n;
vector<vector<int>> adj;
vector<bool> visited;
vector<int> parent;
int cycle_start, cycle_end;

bool dfs(int v, int par) { // passing vertex and its parent vertex
    visited[v] = true;
    for (int u : adj[v]) {
        if(u == par) continue; // skipping edge to parent vertex
        if (visited[u]) {
            cycle_end = v;
            cycle_start = u;
            return true;
        }
        parent[u] = v;
        if (dfs(u, parent[u]))
            return true;
    }
    return false;
}

void find_cycle() {
    visited.assign(n, false);
    parent.assign(n, -1);
    cycle_start = -1;

    for (int v = 0; v < n; v++) {
        if (!visited[v] && dfs(v, parent[v]))
            break;
    }

    if (cycle_start == -1) {
        cout << "Acyclic" << endl;
    } else {
        vector<int> cycle;
        cycle.push_back(cycle_start);
        for (int v = cycle_end; v != cycle_start; v = parent[v])
            cycle.push_back(v);
        cycle.push_back(cycle_start);
        reverse(cycle.begin(), cycle.end());

        cout << "Cycle found: ";
        for (int v : cycle)
            cout << v << " ";
        cout << endl;
    }
}
```
link to the code<https://cp-algorithms.com/graph/finding-cycle.html>