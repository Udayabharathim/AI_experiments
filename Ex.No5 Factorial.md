# Ex.No: 5   Logic Programming – Factorial of number   
### DATE: 29/08/2024                                                                           
### REGISTER NUMBER : 212222060281
### AIM: 
To  write  a logic program for finding the factorial of given number using SWI-PROLOG. 
### Algorithm:
1. STEP 1: Start the program
2. STEP 2:  Write a rules for finding factorial of given program in SWI-PROLOG.
3.   a)	factorial of 0 is 1 => written as factorial(0,1).
4.   b)	factorial of number greater than 0 obtained by recursively calling the factorial    function.
5. STEP 3: Run the program  to find answer of  query.
6. STEP 4: Stop the program.

### Program:

factorial(0,1).<br>
factorial(A,B) :-  <br>
           A > 0, <br>
           C is A-1,<br>
           factorial(C,D),<br>
           B is A*D.<br>

### Output:
![image](https://github.com/user-attachments/assets/ac07487f-6ad5-4d02-9e92-97085e194dc8)



### Result:
Thus the factorial of given number was found by logic programming. 
