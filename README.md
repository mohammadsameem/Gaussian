# Gaussian Elimination

## AIM:
To write a program to find the solution of a matrix using Gaussian Elimination.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm
1.Input matrix dimensions and initialize augmented matrix and solution vector.
2.Populate the augmented matrix with user inputs.
3.Perform Gaussian elimination to reduce the matrix to upper 
triangular form, ensuring no division by zero.
4.Back substitute to compute solution values for the variables.
5.Print the solution vector formatted to two decimal places.

## Program:
```
import sys

def solve():
    input_data = sys.stdin.read().split()
    if not input_data:
        return
    
    n = int(input_data[0])
    matrix = []
    idx = 1
    for i in range(n):
        row = []
        for j in range(n + 1):
            row.append(float(input_data[idx]))
            idx += 1
        matrix.append(row)

    for k in range(n - 1):
        for i in range(k + 1, n):
            factor = matrix[i][k] / matrix[k][k]
            for j in range(k, n + 1):
                matrix[i][j] -= factor * matrix[k][j]
    x = [0.0] * n
    for i in range(n - 1, -1, -1):
        sum_ax = 0.0
        for j in range(i + 1, n):
            sum_ax += matrix[i][j] * x[j]
        
        x[i] = (matrix[i][n] - sum_ax) / matrix[i][i]
    output = []
    for i in range(n):
        output.append(f"X{i} = {x[i]:.2f}")
        
    print(" ".join(output))

if __name__ == '__main__':
    solve()
```

## Output:
<img width="1920" height="911" alt="image" src="https://github.com/user-attachments/assets/864fdc06-0e73-4e37-9af7-6a5cf232276b" />



## Result:
Thus the program to find the solution of a matrix using Gaussian Elimination is written and verified using python programming.

