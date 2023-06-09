### Exercise: Insertion Sort

Compute the running median of a sequence of numbers. That is, given a stream of numbers, print out the median of the list so far on each new element.

Recall that the median of an even-numbered list is the average of the two middle numbers in a *sorted list*.

For example, given the sequence `[2, 1, 5, 7, 2, 0, 5]`, your algorithm should print out:

```
2
1.5
2
3.5
2
2
2
```

Solution
```py
def place_to_insert(array, key):
    index = 0
    for i in array:
        if i > key:
            break
        else:
            index += 1
    return index

def insert_to_sorted(array, key):
    index = place_to_insert(array, key)
    return array[0:index]+[key]+array[index:]

if __name__ == "__main__":
    array = [2, 1, 5, 7, 2, 0, 5]

    stream = []

    for count, i in enumerate(array, 1):
        stream = insert_to_sorted(stream, i)
        if count % 2 == 1:
            print(f"Median of {stream} : {stream[(count)//2]}")
        else:
            i1 = count//2
            i2 = (count//2) - 1
            print(f"Median of {stream} : {(stream[i1] + stream[i2])/2}")

```


 [Solution](https://github.com/codebasics/data-structures-algorithms-python/blob/master/algorithms/4_InsertionSort/insertion_sort_exercise_solution.py)
