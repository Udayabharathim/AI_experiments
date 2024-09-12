# Ex.No: 4   Implementation of Alpha Beta Pruning 
### DATE:  12/09/2024                                                                     
### REGISTER NUMBER : 212222060281
### AIM: 
Write a Alpha beta pruning algorithm to find the optimal value of MAX Player from the given graph.
### Steps:
1. Start the program
2. Initially  assign MAX and MIN value as 1000 and -1000.
3.  Define the minimax function  using alpha beta pruning
4.  If maximum depth is reached then return the score value of leaf node. [depth taken as 3]
5.  In Max player turn, assign the alpha value by finding the maximum value by calling the minmax function recursively.
6.  In Min player turn, assign beta value by finding the minimum value by calling the minmax function recursively.
7.  Specify the score value of leaf nodes and Call the minimax function.
8.  Print the best value of Max player.
9.  Stop the program. 

### Program:

#Define a large negative and positive value to represent infinity<br/>
INF = float('inf')<br/>

#Alpha-Beta Pruning function<br/>
def alpha_beta_pruning(depth, node_index, maximizing_player, values, alpha, beta):<br/>
    # Base case: leaf node is reached<br/>
    if depth == 3:<br/>
        return values[node_index]<br/>
    
    if maximizing_player:<br/>
        max_eval = -INF<br/>
        # Recur for the two children of the current node<br/>
        for i in range(2):<br/>
            eval = alpha_beta_pruning(depth + 1, node_index * 2 + i, False, values, alpha, beta)<br/>
            max_eval = max(max_eval, eval)<br/>
            alpha = max(alpha, eval)<br/>
            
            # Prune the branch<br/>
            if beta <= alpha:<br/>
                break<br/>
        return max_eval<br/>
    else:<br/>
        min_eval = INF<br/>
        # Recur for the two children of the current node<br/>
        for i in range(2):<br/>
            eval = alpha_beta_pruning(depth + 1, node_index * 2 + i, True, values, alpha, beta)<br/>
            min_eval = min(min_eval, eval)<br/>
            beta = min(beta, eval)<br/>
            
            # Prune the branch<br/>
            if beta <= alpha:<br/>
                break<br/>
        return min_eval<br/>

#Driver code<br/>
if __name__ == "__main__":<br/>
    # This is the terminal/leaf node values of the game tree<br/>
    values = [3, 5, 6, 9, 1, 2, 0, -1]<br/>

    print("Optimal value:", alpha_beta_pruning(0, 0, True, values, -INF, INF))<br/>










### Output:

![image](https://github.com/user-attachments/assets/2fec98fc-6716-4206-b29e-33ed00854511)


### Result:
Thus the best score of max player was found using Alpha Beta Pruning.
