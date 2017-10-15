## Description
Remove all elements from a linked list of integers that have value val.

### Example
Given 1->2->3->3->4->5->3, val = 3, you should return the list as 1->2->4->5



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
	public ListNode removeElements(ListNode head, int val) {
		// write your code here
		ListNode dummy = new ListNode(0);
		dummy.next = head;
		head = dummy.next;
		while(null != head.next){
		    if(val == head.next.val){
		        head.next = head.next.next;
		    }else{
		        head = head.next;
		    }
		}
		return dummy.next;
	}
}
```