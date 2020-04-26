# Matrix Frequencies
Given a matrix of order m*n, find the frequency of even and odd numbers in the matrix.
For example:
```` python
#Given the following inputs
m = 2, n = 3
[[ 9, 11, 3 ], 
[ 4, 12, 2 ]]

#Your function should return the following output:
#Frequency of odd #:  3 (since 9, 11, and 3 are all odd #s)
#Frequency of even #: 3
````
Solution:
The algorithm is simple. We run through every column of the matrix and every row within
each column using variables. For a matrix entry, matrix[i][j], we check to see if it is even
by using the modulo function. We keep a running counter of every even integer we run into and every 
odd integer we run into. 
To make this a little bit challenging, I have eliminated m and n in my solution.
Therefore, my main method only takes in a matrix. As a matrix is an array, we know that the length of the matrix 
will result in the number of columns and the length of every column of the matrix will yield the number of rows.

````python
def main (matrix):
    countereven = 0
    counterodd = 0
    m = len(matrix)
    n = len(matrix[0])
    for i in range (m):
        for j in range (n):
            if matrix[i][j] % 2 == 0:
                countereven = countereven + 1
            elif (matrix[i][j] % 2 == 1):
                counterodd = counterodd + 1
    return "Frequency of even = " + str(countereven) + "\nFrequency of odd = " + str(counterodd)
````
