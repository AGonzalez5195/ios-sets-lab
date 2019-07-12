# Sets lab

## Question 1

Ms. Gabriel Williams is a botany professor at District College. One day, she asked her student Mickey to compute the average of all the plants with distinct heights in her greenhouse.

Input: heights of trees below:
`161 182 161 154 176 170 167 171 170 174`

Output:
`169.375`

```
var nums = [161, 182, 161, 154, 176, 170, 167, 171, 170, 174]

var uniqueNums = Set(nums)

uniqueNums.reduce(0, +)/uniqueNums.count
```

## Question 2

Determine if a String is a pangram. A pangram is a string that contains every letter of the alphabet at least once.

 e.g `"The quick brown fox jumps over the lazy dog"` is a pangram
 e.g `"The quick brown fox jumped over the lazy dog"` is NOT a pangram

```
let alphabet = "abcdefghijklmnopqrstuvwxyz"

let alphabetSet = Set(alphabet)

let string = "The quick brown fox jumps over the lazy dog"

let stringSet = Set(string)

let intersect = alphabetSet.intersection(stringSet)

if intersect.count == alphabet.count {
print("['\(string)'] is a pangram.")
} else {
print("['\(string)'] is not a pangram.")
}
```
## Question 3

The set S originally contains numbers from 1 to n in ascending order. Unfortunately, due to the data error, one of the numbers in the set was duplicated to another number in the set. This results in the repetition of one number and loss of another number in the set.

You are given an array `nums` representing the data status of the set S after the error occurred. Your task is to first find the number occurs twice and then find the number that is missing from the sequence. Return these two values in the form of an array.

 Example 1:
 Input: `nums = [1,2,2,4]`
 Output: `[2,3]`

 Example 2:
 Input: `nums = [1,1]`
 Output: `[1,2]`

 Example 3:
 Input: `nums = [2,2]`
 Output: `[2,1]`
```
var nums = [1,2,2,4]
var countingNums: [Int] = []
var repeated: [Int] = []
var answer: [Int] = []
for n in 1...nums.count {
countingNums.append(n)
}
var set1 = Set(nums)
var set2 = Set(countingNums)
var missingNo = set1.symmetricDifference(set2)

for setNumbers in set1 {
var count = 0
for arrayNumbers in nums {
if setNumbers == arrayNumbers {
count += 1
}
}
if count > 1 {
answer.append(setNumbers)
}
}
for n in missingNo {
answer.append(n)
}
print(answer)


```
## Question 4

Given the 4 arrays of Ints below, create a new array, sorted in ascending order, that contains all the values without duplicates.

```swift
let arr1 = [2, 4, 5, 6, 8, 10, 12]
let arr2 = [1, 2, 3, 4, 5, 6]
let arr3 = [5, 6, 7, 8, 9, 10, 11, 12]
let arr4 = [1, 3, 4, 5, 6, 7, 9]
```
```
let set1 = Set(arr1)
let set2 = Set(arr2)
let set3 = Set(arr3)
let set4 = Set(arr4)

let setCombined1 = set1.union(set2)
let setCombined2 = set3.union(set4)

let finalSet = setCombined1.union(setCombined2)

print(finalSet.sorted())
```

## Question 5

Perform the following set operations on the lists below:

1. Find the intersection and print the result
2. Find the symmetric difference and print the result
3. Find the union and print the result
4. What is the outcome of subtracting `list2` from `list1`? Print the result

```swift
let list1: Set = [1, 3, 4, 6, 2, 7, 9]
let list2: Set = [3, 7, 13, 10, 4]
```
```
//Step 1

print(list1.intersection(list2))

//Step 2

print(list1.symmetricDifference(list2))

//Step 3

print(list1.union(list2))

//Step 4

print(list1.subtracting(list2))
```

## Question 6

What output will be produced by the code below? Select one answer.

```swift
var spaceships = Set()

spaceships.insert("Serenity")
spaceships.insert("Enterprise")
spaceships.insert("TARDIS")
spaceships.insert("Serenity")

print(spaceships.count)
```

- 3 
- 4
- Nothing will be output
- 0
- (This code will not compile)
- 1
- This code will compile but crash

//
Because Swift cannot use type inference on sets, sets must be declared with the proper type annotation. In this case, it is not properly set and so it will not even compile. Properly setting the spaceships variable as a set of strings would be as follows: 
`var spaceships: Set<String> = []`
## Question 7

What output will be produced by the code below?

```swift
var spaceships1 = Set()

spaceships1.insert("Serenity")
spaceships1.insert("Enterprise")
spaceships1.insert("TARDIS")

let spaceships2 = spaceships1

if spaceships1.isSubset(of: spaceships2) {
  print("This is a subset")
} else {
  print("This is not a subset")
}
```

- This code will compile but crash
- "This is not a subset"
- This code will not compile
- "This is a subset"
- Nothing will be output

// Like the previous question, it will also not compile because of the lack of proper type annotation/declaration. 
`var spaceships1: Set<String> = []` 
This is what it would need to be changed to in order for it to work.
