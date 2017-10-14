Given an array of N items, Merge Sort will:
* Merge each pair of individual element (which is by default, sorted) into sorted arrays of 2 elements,
* Merge each pair of sorted arrays of 2 elements into sorted arrays of 4 elements,
* Repeat the process...,
* Final step: Merge 2 sorted arrays of N/2 elements (for simplicity of this discussion, we assume that N is even) to obtain a fully sorted array of N elements.

This is just the general idea and we need a few more details before we can discuss the true form of Merge Sort.  
Merge Sort is a Divide and Conquer sorting algorithm:  

* The divide step is simple: Divide the current array into two halves (perfectly equal if N is even or one side is slightly greater by one element if N is odd) and then recursively sort the two halves.
* The conquer step is the one that does the most work: Merge the two (sorted) halves to form a sorted array, using the merge routine discussed earlier.
```java
public void merge(final int[] arr, final int low, final int mid, final int high) {
        if (arr.length == 1 || arr.length == 0) {
            return;
        }
        //elements are sorted in tow partitions:  [leftIndex, midIndex], [midIndex, rightIndex]
        int N = arr.length;
        int[] sorted = new int[N];
        int left = low;
        int right = mid + 1;
        int bIndex = 0;
        while (left <= mid && right <= high) {
            sorted[bIndex++] = arr[left] < arr[right] ? arr[left++] : arr[right++];
        }
        while (left <= mid) {
            sorted[bIndex++] = arr[left++];
        }
        while (right <= high) {
            sorted[bIndex++] = arr[right++];
        }
        System.arraycopy(sorted, 0, arr, 0, N);
    }
```
