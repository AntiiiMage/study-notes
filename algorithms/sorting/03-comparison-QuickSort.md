
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