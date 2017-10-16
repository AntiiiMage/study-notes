
## Radix

Assumption: If the items to be sorted are Integers with somewhat large range, we can combine Counting Sort idea with Radix Sort to achieve the linear time complexity.

In Radix Sort, we treat each item to be sorted as a string of d digits (we pad Integers that have less than d digits with leading zeroes if necessary).

For the least significant (rightmost) digit to the most significant digit (leftmost), we pass through the N items and put them according to the active digit into 10 Queues (one for each digit [0..9]), which is like a modified Counting Sort as this one preserves stability. Then we re-concatenate the groups again for subsequent iteration.

Try Radix Sort on the example array above for clearer explanation.

Notice that we only perform O(d × (N+k)) iterations. In this example, d = 4 and k = 10.