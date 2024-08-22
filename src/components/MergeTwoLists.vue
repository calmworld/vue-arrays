<!-- 
 You are given the heads of two sorted linked lists list1 and list2.

Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.


Example 1:
Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]

Example 2:
Input: list1 = [], list2 = []
Output: []

Example 3:
Input: list1 = [], list2 = [0]
Output: [0]
 

Constraints:

The number of nodes in both lists is in the range [0, 50].
-100 <= Node.val <= 100
Both list1 and list2 are sorted in non-decreasing order.


/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} list1
 * @param {ListNode} list2
 * @return {ListNode}
 */
var mergeTwoLists = function(list1, list2) {
    
};
-->

<script setup>
import { ref } from 'vue'

const mergeTwoLists = (list1, list2) => {
    let masterList = [];

    while (list1.length && list2.length) {
        if (list1[0] < list2[0]) {
            masterList.push(list1.shift());
        } else {
            masterList.push(list2.shift());
        }
    }

    if (list1.length) {
        masterList = masterList.concat(list1);
    } else {
        masterList = masterList.concat(list2);
    }

    return masterList;
    
}

const list1 = ref([1,2,4]);
const list2 = ref([1,3,4]);
const result = mergeTwoLists(list1.value, list2.value);
console.log(result);

</script>

<template>
    <div>
        <h1>Merge Two Lists</h1>
        <p>
            You are given the heads of two sorted linked lists list1 and list2.
            Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.
            Return the head of the merged linked list.
        </p>
        <p>Example Input: list1 = [1,2,4], list2 = [1,3,4]:</p>
        <p>Result: {{ mergeTwoLists([1,2,4], [1,3,4]) }}</p>
        <p>Example Input: list1 = [], list2 = []:</p>
        <p>Result: {{ mergeTwoLists([], []) }}</p>
    </div>
</template>
