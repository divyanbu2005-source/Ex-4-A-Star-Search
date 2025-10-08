<h1>ExpNo 4 : Implement A* search algorithm for a Graph</h1> 
<h3>Name:Divya A       </h3>
<h3>Register Number:      2305002007     </h3>
<H3>Aim:</H3>
<p>To ImplementA * Search algorithm for a Graph using Python 3.</p>
<H3>Algorithm:</H3>


Step 1: Start with the start node.

Step 2: Keep a list of nodes to check called open_list, initially containing only the start node.

Step 3: Keep track of the cost to reach each node in a dictionary g, with the start node cost = 0.

Step 4: Keep a parent dictionary to remember the path, with parent of start = None.

Step 5: While the open_list is not empty:

Pick the node with the smallest total cost (cost so far + estimated cost to goal).

If this node is the goal, follow parent nodes backward to get the path and stop.

Remove this node from the open_list.

Step 6: For each neighbor of the current node:

Calculate new cost = cost to current node + edge cost.

If the neighbor is not in the cost dictionary or the new cost is smaller than the previous one:

Update the cost for that neighbor.

Set the parent of the neighbor to the current node.

Add the neighbor to the open_list with total cost = new cost + heuristic value.

Step 7: Repeat Steps 5 and 6 until the open_list is empty or the goal is reached.

Step 8: If the goal node is found, display the path (from start to goal).
Otherwise, print “No path found.”
## PROGRAM
```

import heapq

def astar(g,s,t,h):
    q=[(h[s],0,s,[])]
    v=set()
    while q:
        f,gc,u,p=heapq.heappop(q)
        if u==t: return p+[u]
        if u in v: continue
        v.add(u)
        for x,c in g.get(u,[]): 
            if x not in v: heapq.heappush(q,(gc+c+h.get(x,0),gc+c,x,p+[u]))
    return None

g={}
print("Input edges as: node1 node2 cost (type 'done' when finished):")
while (e:=input())!="done":
    u,v,c=e.split();g.setdefault(u,[]).append((v,int(c)))

h={u:int(input(f"Heuristic for {u}: ")) for u in g}
s=input("Start node: ");t=input("Goal node: ")
print("Path:",astar(g,s,t,h) or "No path found")


```

## SAMPLE GRAPH 
<img width="899" height="905" alt="image" src="https://github.com/user-attachments/assets/190a23e6-ca69-4a64-a309-fe814eb64a2c" />


## SAMPLE INPUT

A B 3

A D 5

B C 4

C E 6

D F 1

E F 2


## SAMPLE OUTPUT

<img width="943" height="702" alt="image" src="https://github.com/user-attachments/assets/48045b24-ab5a-4d2d-9052-afbbedf470d4" />


## RESULT
Thus, the program successfully finds the shortest path from the start node to the goal node using the A* algorithm.


