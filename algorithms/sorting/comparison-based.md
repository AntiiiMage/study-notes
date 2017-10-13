We will discuss three comparison-based sorting algorithms in the next few slides:
### Bubble Sort,
### Selection Sort,
### Insertion Sort.
They are called comparison-based as they compare pairs of elements of the array and decide whether to swap them or not.
These three sorting algorithms are the easiest to implement but also not the most efficient, as they run in ##O(N2)##.
# Bubble Sorting
```
do
  swapped = false
  for i = 1 to indexOfLastUnsortedElement-1
    if leftElement > rightElement
      swap(leftElement, rightElement)
      swapped = true
while swapped
```
