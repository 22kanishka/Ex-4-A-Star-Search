<h1>ExpNo 4 : Implement A* search algorithm for a Graph</h1> 
<h3>Name: V.S.Sree Viveka      </h3>
<h3>Register Number: 2305001031        </h3>
<H3>Aim:</H3>
<p>To ImplementA * Search algorithm for a Graph using Python 3.</p>
<H3>Algorithm:</H3>


// A* Search Algorithm
1. Start with the start node.
2. Keep a list of nodes to check called open_list, initially containing only the start node.
3. Keep track of the cost to reach each node in a dictionary g, with start node cost = 0.
4. Keep a parent dictionary to remember the path, with parent of start = None.
5. While the open_list is not empty:

   * Pick the node with the smallest total cost (cost so far + estimated cost to goal).
   * If this node is the goal, follow parent nodes backward to get the path and stop.
   * Remove this node from the open_list.
   * For each neighbor of this node:

     * If the neighbor is not visited yet, or a cheaper path is found:

       * Update its cost and parent.
       * Add it to the open_list if not already there.
6. If the open_list becomes empty and the goal was not reached, there is no path.
## PROGRAM
```python
def a_star(start, goal, graph, h):
    open_list = [start]
    g = {start: 0}
    parent = {start: None}

    while open_list:
        n = min(open_list, key=lambda x: g[x] + h[x])
        if n == goal:
            path = []
            while n:
                path.append(n)
                n = parent[n]
            return path[::-1]

        open_list.remove(n)
        for m, cost in graph.get(n, []):
            if m not in g or g[m] > g[n] + cost:
                g[m] = g[n] + cost
                parent[m] = n
                if m not in open_list:
                    open_list.append(m)
    return None

# --- User Input for graph ---
graph = {}
h = {}

nodes = input("Enter all nodes separated by space: ").split()

for node in nodes:
    h[node] = int(input(f"Heuristic value for {node}: "))
    graph[node] = []
    n = int(input(f"How many neighbors does {node} have? "))
    for _ in range(n):
        neighbor = input("  Enter neighbor node 1: ")
        cost = int(input(f"  Enter cost to reach {neighbor}: "))
        graph[node].append((neighbor, cost))

start = input("Enter start node: ")
goal = input("Enter goal node: ")

path = a_star(start, goal, graph, h)
print("Path found:", path)
```

SAMPLE GRAPH I
![WhatsApp Image 2025-10-03 at 09 22 57_c1b83572](https://github.com/user-attachments/assets/a620a08b-1339-4cec-9d52-3f9b560e4792)

SAMPLE INPUT
![WhatsApp Image 2025-10-03 at 09 51 02_de0ff9a2](https://github.com/user-attachments/assets/e7dd60dc-ffc6-4fba-bef0-de17e6af1e3c)

<hr>
Sample Output

![WhatsApp Image 2025-10-03 at 09 51 51_f48a4a9d](https://github.com/user-attachments/assets/634ebd83-86a8-4ac1-94cc-b45b7b32d0c3)

<hr>
##RESULT:
Thus the given program for A* algorithm was implemented and executed successfully.

