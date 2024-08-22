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

// Solution 1:

// const mergeTwoLists = (list1, list2) => {
//     let masterList = [];

//     while (list1.length && list2.length) {
//         if (list1[0] < list2[0]) {
//             masterList.push(list1.shift());
//         } else {
//             masterList.push(list2.shift());
//         }
//     }

//     if (list1.length) {
//         masterList = masterList.concat(list1);
//     } else {
//         masterList = masterList.concat(list2);
//     }
//     return masterList;  
// }


// Solution 2:

// Time complexity: O(m+n) === m is length of list1 and n is length of list2

// Space complexity: O(1)

const ListNode = function(val, next) {
    this.val = (val === undefined ? 0 : val);
    this.next = (next === undefined ? null : next);
}

const mergeTwoLists = (list1, list2) => {
    let masterlist = new ListNode();
    let current = masterlist;

    while (list1 && list2) {
        if (list1.val > list2.val) {
            current.next = list2;
            list2 = list2.next;
        } else {
            current.next = list1;
            list1 = list1.next;
        }
        current = current.next;
    }

    current.next = list1 || list2;
    return masterlist.next;
}

const arrayToList = (arr) => {
    let dummy = new ListNode();
    let current = dummy;
    for (let val of arr) {
        current.next = new ListNode(val);
        current = current.next;
    }
    return dummy.next;
}

const list1 = ref(arrayToList([1,2,4]));
const list2 = ref(arrayToList([1,3,4]));
const result = ref(mergeTwoLists(list1.value, list2.value));

// Convert the result linked list back to an array for easy comparison
const listToArray = (list) => {
    let arr = [];
    while (list) {
        arr.push(list.val);
        list = list.next;
    }
    return arr;
}
// expected result: [1,1,2,3,4,4]
console.log(listToArray(result.value)); // [1,1,2,3,4,4]

</script>

<template>
    <div>
        <h1>Merge Two Lists</h1>
        <p>
            You are given the heads of two sorted linked lists list1 and list2.
            Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.
            Return the head of the merged linked list.
        </p>
        <h3>Example Input: list1 = [1,2,4], list2 = [1,3,4]:</h3>
        <p>Output should be: [1,1,2,3,4,4]</p>
        <p>Result: {{ listToArray(result) }}</p>
        <h3>Example Input: list1 = [], list2 = []:</h3>
        <p>Output should be: []</p>
        <p>Result: {{ listToArray(mergeTwoLists([], [])) }}</p>
        <h3>Example Input: list1 = [], list2 = [0]:</h3>
        <p>Output should be: [0]</p>
        <p>Result: {{ listToArray(mergeTwoLists([], [0])) }}</p>
    </div>
</template>
