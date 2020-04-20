# Check whether two arrays are equal
Given two arrays, write a function in vanilla Python (e.g., no libraries) 
to check whether or not the arrays are equal. You can consider the two arrays equal 
if both of them contain the same set of elements - the order of elements can differ.

For example,
````python
#Given the following:
arr1 = [1,5,6,7,8,0]
arr2 = [0,5,7,6,8,1]

#output = Yes
arr3 = [1,5,6,7,8,0]
arr4 = [0,7,7,7,8,1]
````

Solution:
Let's take a minute and think about how we can make sure that two arrays are equal. If the elements of the arrays matched perfectly, then we would just need to check if arr1(i) = arr2(i), where i starts at 0 and iterates through the length of either arr1 or arr2 (Arrays can only be compared if they have the same length; if they don't, we reject by default). How can we make them match perfectly?

We can sort them first. This will make all of the elements align in order. 
Then, we can check to see if arr1(i) = arr2(i).
Let's implement this below:
````python
def quick_sort(arr,low,high): 
    if low < high: 
        #pi = partition(arr,low,high)
        i = low-1
        pivot = arr[high]
        for j in range(low, high):
            if arr[j] <= pivot:
                i += 1
                arr[i], arr[j] = arr[j], arr[i]
            arr[i+1], arr[high] = arr[high], arr[i+1]
        quick_sort(arr, low, i) 
        quick_sort(arr, i+1, high) 
        return arr
        
def main (arr1, arr2):
    if len(arr1) != len(arr2):
        return "not equal"
    else:
        quick_sort(arr1, 0, len(arr1)-1), quick_sort(arr2, 0, len(arr2)-1)
        for i in range(len(arr1)):
                if (arr1[i] != arr2[i]):
                    return "not equal"
    return "equal"
````
