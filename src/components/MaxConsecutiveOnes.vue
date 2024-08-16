<script setup>
import { ref } from 'vue'

const findMaxConsecutiveOnes = (nums) => {
    let max = 0;
    let count = 0;
    
    for (let i = 0; i < nums.length; i++) {
        if (nums[i] === 1) {
            count++;
            max = Math.max(max, count);
        } else {
            count = 0;
        }
    }
    
    return max;
}

// const nums = ref([1,0,1,1,0,1]);
// const result = ref(findMaxConsecutiveOnes(nums.value));
</script>

<template>
    <div>
        <h1>Max Consecutive Ones</h1>
        <h2>Given a binary array nums, return the maximum number of consecutive 1's in the array.</h2>
        <h4>Example A: [1,1,0,1,1,1]</h4>
        <p>Result: {{ findMaxConsecutiveOnes([1,1,0,1,1,1]) }}</p>
        <h4>Example B: [1,0,1,1,0,1]</h4>
        <p>Result: {{ findMaxConsecutiveOnes([1,0,1,1,0,1]) }}</p>
    </div>
</template>

<style scoped>
h1 {
    color: #333;
}
</style>

<style scoped>
h1 {
    color: #333;
}
</style>





<!-- 

// Max Consecutive Ones

/*

Given a binary array nums, return the maximum number of consecutive 1's in the array.


Example 1:

Input: nums = [1,1,0,1,1,1]
Output: 3
Explanation: The first two digits or the last three digits are consecutive 1s. The maximum number of consecutive 1s is 3.

Example 2:

Input: nums = [1,0,1,1,0,1]
Output: 2
 

Constraints:

1 <= nums.length <= 105
nums[i] is either 0 or 1.


*/

/**
 * @param {number[]} nums
 * @return {number}
 */
var findMaxConsecutiveOnes = function(nums) {

    let max = 0;
    let count = 0;
    
    for (let i = 0; i < nums.length; i++) {
        if (nums[i] === 1) {
            count++;
            max = Math.max(max, count);
        } else {
            count = 0;
        }
    }
    
    return max;
    
}; -->