### Binary Search Exercise
1. When I try to find number 5 in below list using binary search, it doesn't work and returns me -1 index. Why is that?

    ```numbers = [1,4,6,9,10,5,7]```

   Solution:
   Because numbers is not a sorted list/array
    
1. Find index of all the occurances of a number from sorted list

    ```
    numbers = [1,4,6,9,11,15,15,15,17,21,34,34,56]
    number_to_find = 15  
    ```
   This should return 5,6,7 as indices containing number 15 in the array

Solution
```py
def binary_search(numbers, val):
    left_index = 0
    right_index = len(numbers) - 1

    while left_index <= right_index:
        mid_index = (left_index + right_index) // 2
        mid_number = numbers[mid_index]

        if mid_number == val:
            return mid_index
        elif mid_number < val:
            left_index = mid_index + 1
        else:
            right_index = mid_index - 1

    return -1

def all_occur(numbers, val):
    index = binary_search(numbers, val)
    if index == -1:
        return []

    occur = [index]
    # Check to the left of the found index
    i = index - 1
    while i >= 0 and numbers[i] == val:
        occur.append(i)
        i -= 1

    # Check to the right of the found index
    i = index + 1
    while i < len(numbers) and numbers[i] == val:
        occur.append(i)
        i += 1

    return sorted(occur)


```

       
    
[Solution](https://github.com/codebasics/data-structures-algorithms-python/blob/master/algorithms/1_BinarySearch/binary_search_exercise_solution.py)    
