
## Lower bound of sorting algrithm

Any comparison-based sorting algorithm with worst-case complexity O(N log N), like Merge Sort is considered an optimal algorithm, i.e. we cannot do better than that.

However, we can achieve faster sorting algorithm — i.e. in O(N) — if certain assumptions of the input array exist and thus we can avoid comparing the items to determine the sorted order.

## Counting Sort
### Assumption
If the items to be sorted are Integers with small range, we can count the frequency of occurrence of each Integer (in that small range) and loop through that small range to output the items in sorted order.

### Demonstration
For example, an array where all Integers are within [1..9], thus we just need to count how many times Integer 1 appears, Integer 2 appears, ..., Integer 9 appears, and then loop through 1 to 9 to print out x copies of Integer y if frequency[y] = x.

The time complexity is O(N) to count the frequencies and O(k) where k is the range of the input Integers, which is 9-1+1 = 9 in this example. The time complexity of Counting Sort is O(N+k) which is O(N) if k is (very) small.

We will not be able to do the counting part of Counting Sort when k is relatively big due to memory limitation.