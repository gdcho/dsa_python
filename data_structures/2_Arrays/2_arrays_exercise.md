# Exercise: Array DataStructure

1. Let us say your expense for every month are listed below,
	1. January -  2200
 	2. February - 2350
    3. March - 2600
    4. April - 2130
    5. May - 2190

Create a list to store these monthly expenses and using that find out,

    1. In Feb, how many dollars you spent extra compare to January?
    2. Find out your total expense in first quarter (first three months) of the year.
    3. Find out if you spent exactly 2000 dollars in any month
    4. June month just finished and your expense is 1980 dollar. Add this item to our monthly expense list
    5. You returned an item that you bought in a month of April and
    got a refund of 200$. Make a correction to your monthly expense list
    based on this
    
My solution:
```sh
1. dict = {'January': 2200, 'February': 2350, 'March': 2600, 'April': 2130, 'May': 2190}
or 
   list = [2200, 2350, 2600, 2130, 2190]
   
print(dict['February']-dict['January']) or print(list[1]-list[0])
2. print(dict['January']+['February']+['March']) or print(list[0]+list[1]+list[2])
3. print(2000 in list) or print(2000 in dict.values())
4. list.append(1980) or dict['July'] = 1980
5. list[3] = 2130 - 20 or dict['April'] = dict['April'] - 20
```

[Solution](https://github.com/codebasics/data-structures-algorithms-python/blob/master/data_structures/2_Arrays/Solution/1_expenses.py)

2. You have a list of your favourite marvel super heros.
```
heros=['spider man','thor','hulk','iron man','captain america']
```

Using this find out,

    1. Length of the list
    2. Add 'black panther' at the end of this list
    3. You realize that you need to add 'black panther' after 'hulk',
       so remove it from the list first and then add it after 'hulk'
    4. Now you don't like thor and hulk because they get angry easily :)
       So you want to remove thor and hulk from list and replace them with doctor strange (because he is cool).
       Do that with one line of code.
    5. Sort the heros list in alphabetical order (Hint. Use dir() functions to list down all functions available in list)

My solution:
```sh
1. len(heros)
2. heros.append('black panther')
3. heros.pop(-1) or heros.remove('black panther') then heros.insert(3, 'black panther')
4. heros[1:3]=['doctor strange']
5. print(sorted(heros))
```

[Solution](https://github.com/codebasics/data-structures-algorithms-python/blob/master/data_structures/2_Arrays/Solution/2_marvel.py)


3. Create a list of all odd numbers between 1 and a max number.
Max number is something you need to take from a user using input() function

My solution:
```sh
max = int(input("Ener max number"))
odd = []
for x in range(1, max):
	if x % 2 != 0:
		odd.append(x)
print(odd)
```

[Solution](https://github.com/codebasics/data-structures-algorithms-python/blob/master/data_structures/2_Arrays/Solution/3_odd_even_numbers.py)

