# Exercise: Shell Sort

Sort the elements of a given list using shell sort, but with a slight modification. Remove all the repeating occurances of elements while sorting. 

Traditionally, when comparing two elements in shell sort, we swap if first element is bigger than second, and do nothing otherwise.

 In this modified shell sort with duplicate removal, we will swap if first element is bigger than second, and do nothing if element is smaller, but if values are same, we will delete one of the two elements we are comparing before starting the next pass for the reduced gap.



For example, given the unsorted list `[2, 1, 5, 7, 2, 0, 5, 1, 2, 9, 5, 8, 3]`, after sorting using shell sort without duplicates, the sorted list would be:

```
[0, 1, 2, 3, 5, 7, 8, 9]
```

Solution
```py
def shell_sort(arr):
    size = len(arr)
    gap = size // 2
    unique_values = set()  # keeps track of the unique elements

    while gap > 0:
        for i in range(gap, size):
            anchor = arr[i]
            j = i
            while j >= gap and arr[j-gap] > anchor:
                if arr[j-gap] not in unique_values:  # new unique value
                    unique_values.add(arr[j-gap])
                    arr[j] = arr[j-gap]
                    j -= gap
                else:  # duplicate value
                    del arr[j]
                    size -= 1
                    if j >= gap:
                        j -= gap
            arr[j] = anchor
        gap = gap // 2

if __name__ == '__main__':
    tests = [
        [89, 78, 61, 53, 23, 21, 17, 12, 9, 7, 6, 2, 1],
        [],
        [1,5,8,9],
        [234,3,1,56,34,12,9,12,1300],
        [5]
    ]
    for elements in tests:
        shell_sort(elements)
        print(elements)

```

 [Solution](https://github.com/codebasics/data-structures-algorithms-python/blob/master/algorithms/6_ShellSort/shell_sort_exercise_solution.py)
