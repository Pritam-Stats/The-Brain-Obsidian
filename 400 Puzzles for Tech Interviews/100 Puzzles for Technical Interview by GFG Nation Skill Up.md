## 1. Measure 4 litre with 3 and 5 litre bottle
You have two bottles:  One of 3L and another of 5L.
- Goal is to measure out precisely 4 liters of water using only these two bottles, with no additional measuring devices or markings available on the bottles.
- You can fill the bottles to their full capacity, empty them completely, or pour water from one bottle to the other until one is full or the other is empty.

By relying solely on clever pouring strategies and logical thinking, how can you achieve exactly 4 liters of water in one of the bottles?
![water-measure-main](https://media.geeksforgeeks.org/wp-content/uploads/20250719165145253491/water-measure-main.webp)

### Approach 1
1. Full the 5L bottle
2. Pour the 3L bottle from the 5L bottle.
3. 5L bottle will left with 2l water and empty the 3L bottle.
4. Now, transfer the 2L water to the empty 3L bottle.
5. Full the 5L bottle again.
6. Now there is a space of 1L on the 3L bottle, fill that from the 5L bottle.
7. Now we left with 4L water on the 5L bottle
### Approach 2
![water-measure-2-1.webp](https://media.geeksforgeeks.org/wp-content/uploads/20250719165454966112/water-measure-2-1.webp)

![water-measure-2-2.webp](https://media.geeksforgeeks.org/wp-content/uploads/20250719165501752896/water-measure-2-2.webp)

## 2. Find the Ages of Three Daughters
***Alok*** has three daughters. His friend ***Shyam*** wants to know the ages of his daughters. Alok gives him a first hint. 

***1.*** The product of their age is 72.   
***Shyam*** says this is not enough information. ***Alok*** gives him a second hint.   
  
***2.*** The sum of their ages is equal to my house number.   
***Shyam*** goes out and looks at the house number and says, “I still do not have enough information to determine the ages”. ***Alok*** admits that ***Shyam*** can not guess and gives him the third hint.   
  
***3.*** The oldest girl likes strawberry ice cream.   
***Shyam*** can guess after the third hint. Can you guess what are the ages of the three daughters?

### Approach
1. Find all possible triplets whose product will be 72.
```Python
	ans = []
for i in range(73):
for j in range(i, 73):
for k in range(j, 73):
if i*j*k == 72:
ans.append([i,j,k])
print(ans)

print(len(ans))
```

- There are 12 possible triplets.
2. Now Sum is the house number. The hint is *House number is unique*. Find the sums of all the triplets
```Python
house_num = []
ans2 = []
for triplet in ans:
if sum(triplet) in house_num:
ans2.append(triplet)

house_num.append(sum(triplet))
```

- only two triplets has same sum.
3. Now since it has been said *The Oldest* one, so there is 1 of highest age. the ans is `3,3,8`


## 3. 