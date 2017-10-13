We will discuss three comparison-based sorting algorithms in the next few slides:
* Bubble Sort,
* Selection Sort,
* Insertion Sort.

They are called comparison-based as they compare pairs of elements of the array and decide whether to swap them or not.

These three sorting algorithms are the easiest to implement but also not the most efficient, as they run in **O(N^2)**.  
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
# Selection Sort
Total: O(N2) 
```
void selectionSort(int a[], int N){
  for(int L = 0; L < N - 1; L++){ // O(N)
    find the position of the minimum element X ∈ [L..N-1] // O(N)
    swap(X, L) // O(1), note that X may be equal to L (no actual swap)
  }
}
```
# Insert Sort
Insertion sort is similar to how most people arrange a hand of poker cards:  
* Start with one card in your hand,
* Pick the next card and insert it into its proper sorted order,
* Repeat previous step for all cards.
```
void insertionSort(int a[], int N) {
  for (int i = 1; i < N; i++) { // O(N)
    X = a[i]; // X is the item to be inserted
    for (j = i-1; j >= 0 && a[j] > X; j--) // can be fast or slow
      a[j+1] = a[j]; // make a place for X
    a[j+1] = X; // this is the insertion point
  }
}
```
The outer loop executes N−1 times, that's quite clear.  

But the number of times the inner-loop is executed depends on the input:  
* In best-case scenario, the array is already sorted and (a[j] > X) is always false
So no shifting of data is necessary and the inner loop runs in O(1),  
* In worst-case scenario, the array is reverse sorted and (a[j] > X) is always true
Insertion always occur at the front of the array and the inner loop runs in O(N).  

Thus, the best-case time is O(N × 1) = O(N) and the worst-case time is O(N × N) = O(N2).


