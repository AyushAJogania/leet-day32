# leet-day32

# Partition List

## Problem Statement

Given the head of a linked list and a value `x`, partition it such that all nodes less than `x` come before nodes greater than or equal to `x`. You should preserve the original relative order of the nodes in each of the two partitions.

## Example

### Input

```
head = [1,4,3,2,5,2], x = 3
```

### Output

```
[1,2,2,4,3,5]
```

## Approach

To solve this problem, we can maintain two separate linked lists, one for nodes less than `x` and one for nodes greater than or equal to `x`. We'll traverse the original linked list and keep adding nodes to their respective lists based on the value of `x`. Finally, we'll concatenate the two lists and return the result.

## Algorithm

1. Initialize two dummy nodes: `lessDummy` for the list of nodes less than `x` and `greaterDummy` for the list of nodes greater than or equal to `x`.
2. Initialize two pointers: `lessPtr` to keep track of the end of the list of nodes less than `x` and `greaterPtr` to keep track of the end of the list of nodes greater than or equal to `x`.
3. Traverse the original linked list using the `head` pointer:
   - If the current node's value is less than `x`, add it to the `lessPtr` and move the `lessPtr` to the next node.
   - If the current node's value is greater than or equal to `x`, add it to the `greaterPtr` and move the `greaterPtr` to the next node.
4. Connect the end of the `lessDummy` list to the beginning of the `greaterDummy` list.
5. Connect the end of the `greaterDummy` list to `nullptr`.
6. Return the `lessDummy.next`, which is the head of the partitioned linked list.

## Complexity Analysis

- Time complexity: O(n), where n is the number of nodes in the linked list.
- Space complexity: O(1), as we are not using any additional data structures except for a few pointers.

## Implementation

Here's the implementation of the approach in C++:

```cpp
class Solution {
public:
    ListNode* partition(ListNode* head, int x) {
        ListNode lessDummy(0);
        ListNode greaterDummy(0);
        ListNode *lessPtr = &lessDummy, *greaterPtr = &greaterDummy;
        
        while (head) {
            if (head->val < x) {
                lessPtr->next = head;
                lessPtr = lessPtr->next;
            } else {
                greaterPtr->next = head;
                greaterPtr = greaterPtr->next;
            }
            head = head->next;
        }
        
        lessPtr->next = greaterDummy.next;
        greaterPtr->next = nullptr;
        
        return lessDummy.next;
    }
};
```

## Conclusion

Partitioning a linked list based on a given value can be achieved efficiently by maintaining two separate lists and merging them. The provided C++ solution demonstrates this approach, offering an optimal solution to the problem.
