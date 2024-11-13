# Ex.No: 1  Implementation of Breadth First Search 
### DATE:  08/08/2024                                                                          
### REGISTER NUMBER : 212222060281
### AIM: 
To write a python program to implement Breadth first Search. 
### Algorithm:
1. Start the program
2. Create the graph by using adjacency list representation
3. Define a function bfs and take the set “visited” is empty and “queue” is empty
4. Search start with initial node and add the node to visited and queue.
5. For each neighbor node, check node is not in visited then add node to visited and queue list.
6.  Creating loop to print the visited node.
7.   Call the bfs function by passing arguments visited, graph and starting node.
8.   Stop the program.
### Program:
#breadth first Search in python </br>
graph = {</br>
 'A' : ['B','C'],</br>
 'B' : ['D', 'E'],</br>
 'C' : ['F'],</br>
 'D' : [],</br>
 'E' : ['F'],</br>
 'F' : []</br>
 }</br>
visited = [] # List for visited nodes.</br>
queue = []     #Initialize a queue</br>
def bfs(visited, graph, node): #function for BFS</br>
    visited.append(node)</br>
    queue.append(node)</br>
    while queue:          # Creating loop to visit each node</br>
        m = queue.pop(0)</br>
        print (m)</br>
        for neighbour in graph[m]:</br>
            if neighbour not in visited:</br>
                visited.append(neighbour)</br>
                queue.append(neighbour)</br>

### Driver Code</br>
print("Following is the Breadth-First Search")</br>
bfs(visited, graph, 'A')    # function calling</br>



### Output:

![image](https://github.com/user-attachments/assets/55f43176-ebc2-47e7-859d-d395b518ad86)


### Result:
Thus the breadth first search order was found sucessfully.
