# Ex.No: 3  Implementation of Minimax Search
### DATE: 12/09/2024                                                                        
### REGISTER NUMBER : 212222060281
### AIM: 
Write a mini-max search algorithm to find the optimal value of MAX Player from the given graph.
### Algorithm:
1. Start the program
2. import the math package
3. Specify the score value of leaf nodes and find the depth of binary tree from leaf nodes.
4. Define the minimax function
5. If maximum depth is reached then get the score value of leaf node.
6. Max player find the maximum value by calling the minmax function recursively.
7. Min player find the minimum value by calling the minmax function recursively.
8. Call the minimax function  and print the optimum value of Max player.
9. Stop the program. 

### Program:
import math<br/>
def minimax (curDepth, nodeIndex,<br/>
             maxTurn, scores,<br/>
             targetDepth):<br/>
    # base case : targetDepth reached<br/>
    if (curDepth == targetDepth):<br/>
        return scores[nodeIndex]<br/>
    if (maxTurn):<br/>
        return max(minimax(curDepth + 1, nodeIndex * 2,<br/>
                    False, scores, targetDepth),<br/>
                   minimax(curDepth + 1, nodeIndex * 2 + 1,<br/>
                    False, scores, targetDepth))<br/>
     <br/>
    else:<br/>
        return min(minimax(curDepth + 1, nodeIndex * 2,<br/>
                     True, scores, targetDepth),<br/>
                   minimax(curDepth + 1, nodeIndex * 2 + 1,<br/>
                     True, scores, targetDepth))<br/>
     
# Driver code
scores = [3, 5, 2, 9, 12, 5, 23, 20]<br/>
treeDepth = math.log(len(scores), 2) # calculate depth of node  log 8 (base 2) = 3)<br/>
print("The optimal value is : ", end = "")<br/>
print(minimax(0, 0, True, scores, treeDepth))<br/>












### Output:


![Screenshot 2024-09-12 091434](https://github.com/user-attachments/assets/47e320d8-0349-4bc0-b971-3af5a083606e)

### Result:
Thus the optimum value of max player was found using minimax search.
