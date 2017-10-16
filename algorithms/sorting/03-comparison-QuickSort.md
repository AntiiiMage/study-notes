
### Quick Sort as D&C 
Divide step: 
* Choose an item p (known as the pivot)
* Then partition the items of a[i..j] into three parts: a[i..m-1], a[m], and a[m+1..j].
* a[i..m-1] (possibly empty) contains items that are smaller than p.
* a[m] is the pivot p, i.e. index m is the correct position for p in the sorted order of array a.
* a[m+1..j] (possibly empty) contains items that are greater than or equal to p.
* Then, recursively sort the two parts.  

Conquer step: Don't be surprised... Do Nothing :O!  
If you compare this with Merge Sort, you will see that Quick Sort D&C steps are totally opposite with Merge Sort.


## Quick Sort Implementation
```java
public void quickSort(final int[] arr, final int start, final int end) {
    if (start < end) {
        int storeIndex = partition(arr, start, end);
        quickSort(arr, start, storeIndex - 1);
        quickSort(arr, storeIndex + 1, end);
    }

}

public int partition(final int[] arr, final int start, final int end) {
    int pivot = arr[start];
    int storeIndex = start; //partition1 and partition2 are initially empty
    for (int i = start + 1; i <= end; i++) {
        if (arr[i] < pivot) { // put smaller value in arr[i] into arr[start...storeIndex - 1]
            swap(arr, storeIndex + 1, i);
            storeIndex++; // increment storeIndex to be the end index of smaller partition
        }
    }
    swap(arr, start, storeIndex);
    return storeIndex;
}
```

## Analysis

First, we analyze the cost of one call of partition.

Inside partition(a, i, j), there is only a single for-loop that iterates through (j-i) times. As j can be as big as N-1 and i can be as low as 0, then the time complexity of partition is O(N).

Similar to Merge Sort analysis, the time complexity of Quick Sort is then dependent on the number of times partition(a, i, j) is called.

When the array a is already in ascending order, like the example above, Quick Sort will set p = a[0] = 5, and will return m = 0, thereby making S1 region empty and S2 region: Everything else other than the pivot (N-1 items).

## Worst Case analysis of Quick Sort
{1, ,28, 33, 349, 999}  
On such worst case input scenario, this is what happens:

The first partition takes O(N) time, splits a into 0, 1, N-1 items, then recurse right.  
The second one takes O(N-1) time, splits a into 0, 1, N-2 items, then recurse right again.  
...  
Until the last, N-th partition splits a into 0, 1, 1 item, and Quick Sort recursion stops.

This is the classic N+(N-1)+(N-2)+...+1 pattern, which is O(N^2)

## Best Case analysis
The best case scenario of Quick Sort occurs when partition always splits the array into two equal halves, like Merge Sort.

When that happens, the depth of recursion is only log n.

As each level takes O(N) comparisons, the time complexity is O(N log N).

## Random Quick Sort
Same as Quick Sort except just before executing the partition algorithm, it randomly select the pivot between a[low..high] instead of always choosing a[low] deterministically.  

Just imagine that on randomized version of Quick Sort that randomizes the pivot selection, we will not always get extremely bad split of 0 (empty), 1 (pivot), and N-1 other items. This combination of lucky (half-pivot-half), somewhat lucky, somewhat unlucky, and extremely unlucky (empty, pivot, the rest) yields an average time complexity of O(N log N) time complexity.