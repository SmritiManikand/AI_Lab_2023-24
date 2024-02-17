# 19CS413- ARTIFICIAL INTELLIGENCE

## AIM
To write a Python program to find the path of visiting all nodes using breadth first search and depth first search.

## REQUIREMENTS 
1. PYTHON
2. SWI-PROLOG
3. PDDL 0R PDDL EDITOR ONLINE
4. JUPITER OR COLAB NOTEBOOK 

## CODE

## BREADTH FIRST SEARCH (BFS)

```
graph = {
 '5' : ['3','7'],
 '3' : ['2', '4'],
 '7' : ['8'],
 '2' : [],
 '4' : ['8'],
 '8' : []
}
visited = [] # List for visited nodes.
queue = []     # Initialize a queue

def bfs(visited, graph, node):
    visited.append(node)
    queue.append(node)
    while queue:
        m = queue.pop(0) 
        print(m) 
        for neighbour in graph[m]:
            if neighbour not in visited:
                visited.append(neighbour)
                queue.append(neighbour)

# Driver Code
print("Following is the Breadth-First Search")
bfs(visited, graph, '5')
```

## DEPTH FIRST SEARCH (DFS)

```
graph = {
  '5' : ['3','7'],
  '3' : ['2', '4'],
  '7' : ['8'],
  '2' : [],
  '4' : ['8'],
  '8' : []
}
visited = set() # Set to keep track of visited nodes of graph.
def dfs(visited, graph, node):
    if node not in visited:
        print (node)
        visited.add(node)
        for neighbour in graph[node]:
            dfs(visited, graph, neighbour)
# Driver Code
print("Following is the Depth-First Search")
dfs(visited, graph, '5')
```

## OUTPUT

## BFS

<img width="248" alt="s2" src="https://github.com/SmritiManikand/AI_Lab_2023-24/assets/113674204/f9b70b5e-2b63-4079-bfc4-84cd9da2541b">

## DFS

<img width="229" alt="s1" src="https://github.com/SmritiManikand/AI_Lab_2023-24/assets/113674204/9806fea1-b0d6-4d31-a434-3e64f3f71d53">

## RESULT
Thus the Python programs are executed to find the path of visiting all nodes using breadth first search and depth first search.
