## Brief
Given an array of N items, Merge Sort will:
* Merge each pair of individual element (which is by default, sorted) into sorted arrays of 2 elements,
* Merge each pair of sorted arrays of 2 elements into sorted arrays of 4 elements,
* Repeat the process...,
* Final step: Merge 2 sorted arrays of N/2 elements (for simplicity of this discussion, we assume that N is even) to obtain a fully sorted array of N elements.

This is just the general idea and we need a few more details before we can discuss the true form of Merge Sort.  

## Divide and Conquer paradigm
Merge Sort is a Divide and Conquer sorting algorithm:  

* The divide step is simple: Divide the current array into two halves (perfectly equal if N is even or one side is slightly greater by one element if N is odd) and then recursively sort the two halves.
* The conquer step is the one that does the most work: Merge the two (sorted) halves to form a sorted array, using the merge routine discussed earlier.

### Sort Implementation
```java
public void mergeSort(int[] arr, int start, int end) {
        if (start < end) {
            //Divide
            int mid = (start + end) / 2; //Divide
            mergeSort(arr, start, mid);
            mergeSort(arr, mid + 1, end);
            merge(arr, start, mid, end); //Conquer
        }
    }
```
### Merge subroutine
```java
public void merge(final int[] arr, final int low, final int mid, final int high) {
        if (low == high) {
            return;
        }
        //elements are sorted in [low, mid], [mid + 1, high]
        int N = high - low + 1;
        int[] sorted = new int[N];
        int left = low;
        int right = mid + 1;
        int bIndex = 0;
        while (left <= mid && right <= high) { //Compare and take min element, increment partition index if taken
            sorted[bIndex++] = arr[left] < arr[right] ? arr[left++] : arr[right++];
        }
        while (left <= mid) {sorted[bIndex++] = arr[left++];} //Leftover, if any
        while (right <= high) {sorted[bIndex++] = arr[right++];} //Rightover, if any
        for (int i = low; i <= high; i++) { //copy
            arr[i] = sorted[i - low];
        }
}
```
## Demonstration
The actual execution of Merge Sort does not split to two subarrays level by level, but it will recursively sort the left subarray first before dealing with the right subarray.

That's it, on the example array {7,2,6,3,8,4,5}, it will recurse to {7,2,6,3}, then {7,2}, then {7} (single element, sorted by default), backtrack, recurse to {2} (sorted), backtrack, then finally merge {7,2} into {2,7}, before it continue processing {6,3} and so on.

## Analysis
In Merge Sort, the bulk of work is done in the conquer/merge step as the divide step does not really do anything (treated as O(1)).

* When we call merge(a, low, mid, high), we process k = (high-low+1) items.
* There will be at most k-1 comparisons.
* There are k moves from original array a to temporary array b and another k moves back.

In total, number of operations inside **merge** operation is < 3k-1 = O(k).
There are log(N) levels and in each level, we perform **Merge** O(N) work, thus the overall time complexity is O( Nlog(N) ). This is an optimal (comparison-based) sorting algorithm.

## Pros and cons
There are however, several not-so-good parts of Merge Sort. 
* It is actually not easy to implement from scratch. 
* It requires additional O(N) storage during merging operation, thus not really memory efficient.
