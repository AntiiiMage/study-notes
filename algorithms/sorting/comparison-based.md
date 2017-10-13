We will discuss three comparison-based sorting algorithms in the next few slides:
### Bubble Sort,
### Selection Sort,
### Insertion Sort.
They are called comparison-based as they compare pairs of elements of the array and decide whether to swap them or not.
These three sorting algorithms are the easiest to implement but also not the most efficient, as they run in **O(N2)**.
# Bubble Sorting
There are two nested loops in (the standard) Bubble Sort.The outer loop runs for exactly N iterations.But the inner loop runs get shorter and shorter:
When i=0, (N−1) iterations (of comparisons and possibly swaps),
When i=1, (N−2) iterations,
...,
When i=(N−2), 1 iteration,
When i=(N−1), 0 iteration.
Thus, the total number of iterations = (N−1)+(N−2)+...+1+0 = N*(N−1)/2
Total time = c*N*(N−1)/2 = O(N^2)
```
do
  swapped = false
  for i = 1 to indexOfLastUnsortedElement-1
    if leftElement > rightElement
      swap(leftElement, rightElement)
      swapped = true
while swapped
```
