# Exercise: Hash Table

1. [nyc_weather.csv](https://github.com/codebasics/data-structures-algorithms-python/blob/master/data_structures/4_HashTable_2_Collisions/Solution/nyc_weather.csv) contains new york city weather for first few days in the month of January. Write a program that can answer following,
    1. What was the average temperature in first week of Jan
    2. What was the maximum temperature in first 10 days of Jan

Figure out data structure that is best for this problem

Solution
```py
arr = []

with open("nyc_weather.csv","r") as file:
    for line in file:
        tokens = line.split(',')
        try:
            temperature = int(tokens[1])
            arr.append(temperature)
        except:
            print("Invalid temperature.Ignore the row")
```
1. Average temperature in first week of Jan
```py
return sum(arr[0:7]) / 7
```
2. Maximum temperature in the first 10 days of Jan
```py
return max(arr[0:10])
```

[Solution](https://github.com/codebasics/data-structures-algorithms-python/blob/master/data_structures/4_HashTable_2_Collisions/Solution/weather_analysis.ipynb)

2. [nyc_weather.csv](https://github.com/codebasics/data-structures-algorithms-python/blob/master/data_structures/4_HashTable_2_Collisions/Solution/nyc_weather.csv) contains new york city weather for first few days in the month of January. Write a program that can answer following,
    1. What was the temperature on Jan 9?
    2. What was the temperature on Jan 4?

Figure out data structure that is best for this problem

Solution
```py
dict = {}

with open("nyc_weather.csv","r") as f:
    for line in f:
        tokens = line.split(',')
        day = tokens[0]
        try:
            temperature = int(tokens[1])
            dict[day] = temperature
        except:
            print("Invalid temperature.Ignore the row")
```
1. What was the temperature on Jan 9?
```py
return dict["Jan 9"] 
```
2. What was the temperature on Jan 4?
```py
return dict["Jan 4"] 
```

[Solution](https://github.com/codebasics/data-structures-algorithms-python/blob/master/data_structures/4_HashTable_2_Collisions/Solution/weather_analysis.ipynb)

3. [poem.txt](https://github.com/codebasics/data-structures-algorithms-python/blob/master/data_structures/4_HashTable_2_Collisions/Solution/poem.txt) Contains famous poem "Road not taken" by poet Robert Frost. You have to read this file in python and print every word and its count as show below. Think about the best data structure that you can use to solve this problem and figure out why you selected that specific data structure.
```
 'diverged': 2,
 'in': 3,
 'I': 8
```
Solution
```py
word_count = {}
with open("poem.txt","r") as f:
    for line in f:
        tokens = line.split(' ')
        for token in tokens:
            token=token.replace('\n','')
            if token in word_count:
                word_count[token]+=1
            else:
                word_count[token]=1

```

[Solution](https://github.com/codebasics/data-structures-algorithms-python/blob/master/data_structures/4_HashTable_2_Collisions/Solution/exercise_poem_find_word_occurances.ipynb)

4. Implement hash table where collisions are handled using linear probing. We learnt about linear probing in the video tutorial. Take the hash table implementation that uses chaining and modify methods to use **linear probing**. Keep MAX size of arr in hashtable as 10.

Solution
```py 
class HashTable:  
    def __init__(self):
        self.MAX = 10 
        self.arr = [None for i in range(self.MAX)]
        
    def get_hash(self, key):
        hash = 0
        for char in key:
            hash += ord(char)
        return hash % self.MAX
    
    def __getitem__(self, key):
        h = self.get_hash(key)
        if self.arr[h] is None:
            return
        prob_range = self.get_prob_range(h)
        for prob_index in prob_range:
            element = self.arr[prob_index]
            if element is None:
                return
            if element[0] == key:
                return element[1]
           
    def __setitem__(self, key, val):
        h = self.get_hash(key)
        if self.arr[h] is None:
            self.arr[h] = (key,val)
        else:
            new_h = self.find_slot(key, h)
            self.arr[new_h] = (key,val)
        print(self.arr)
        
    def get_prob_range(self, index):
        return [*range(index, len(self.arr))] + [*range(0,index)]
    
    def find_slot(self, key, index):
        prob_range = self.get_prob_range(index)
        for prob_index in prob_range:
            if self.arr[prob_index] is None:
                return prob_index
            if self.arr[prob_index][0] == key:
                return prob_index
        raise Exception("Hashmap full")
        
    def __delitem__(self, key):
        h = self.get_hash(key)
        prob_range = self.get_prob_range(h)
        for prob_index in prob_range:
            if self.arr[prob_index] is None:
                return # item not found so return. You can also throw exception
            if self.arr[prob_index][0] == key:
                self.arr[prob_index]=None
        print(self.arr)

```

[Solution](https://github.com/codebasics/data-structures-algorithms-python/blob/master/data_structures/4_HashTable_2_Collisions/Solution/exercise_hash_table_linear_probing.ipynb)

