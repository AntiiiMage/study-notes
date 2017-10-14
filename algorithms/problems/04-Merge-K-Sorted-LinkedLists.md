## Description
Merge k sorted linked lists and return it as one sorted list.

Analyze and describe its complexity.

### Notice
You should do really partition in array nums instead of just counting the numbers of integers smaller than k.

If all elements in nums are smaller than k, then return nums.length

### Example
Given 
```
[
  2->4->null,
  null,
  -1->null
]
``` 
return -1->2->4->null.



## Naive Solution
```java
/**
 * Definition for ListNode.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int val) {
 *         this.val = val;
 *         this.next = null;
 *     }
 * }
 */
public class Solution {

	/**
     * @param lists: a list of ListNode
     * @return: The head of one sorted list.
     */
    public ListNode mergeKLists(List<ListNode> lists) {
        // write your code here
        if (lists.size() == 0) {
            return null;
        }
        return mergeHelper(lists, 0, lists.size() - 1);
    }

    public ListNode mergeHelper(List<ListNode> lists, int start, int end){
        if(start == end) return lists.get(start);
        int mid = (start + end) / 2;
        ListNode left = mergeHelper(lists, start, mid);
        ListNode right = mergeHelper(lists, mid + 1, end);
        return mergeTwoLists(left, right);
    }
}
```
