# Test
# 1-  sawtooth_sequence
- A sawtooth sequence is a sequence of numbers that alternate between increasing and decreasing. In other words, each element is either strictly greater than its neighbouring elements or strictly less than its neighbouring elements.
![image](https://user-images.githubusercontent.com/30151596/162700635-c98365d7-b391-487c-b813-11941d59d8a4.png)
Given an array of integers arr, your task is to count the number of contiguous subarrays that represent a sawtooth sequence of at least two elements.
```
An array made up of adjacent elements from another array.

For example, consider arr = [2, 3, 7]:

[3, 7] is a contiguous subarray of arr
[2, 3, 7] is a contiguous subarray of arr
[7] is a contiguous subarray of arr
[1, 2, 3] is not a contiguous subarray because it contains elements not in arr
[2, 7] is not a contiguous subarray because the elements aren't adjacent in arr
```
Example
- For arr = [9, 8, 7, 6, 5], the output should be solution(arr) = 4. Since all the elements are arranged in decreasing order, it won't be possible to form any sawtooth subarrays of length 3 or more. There are 4 possible subarrays containing two elements, so the answer is 4.

- For arr = [10, 10, 10], the output should be solution(arr) = 0. Since all of the elements are equal, none of subarrays can be sawtooth, so the answer is 0.

- For arr = [1, 2, 1, 2, 1], the output should be solution(arr) = 10.

All contiguous subarrays containing at least two elements satisfy the condition of problem. There are 10 possible contiguous subarrays containing at least two elements, so the answer is 10.
**Input**
An array of integers.
**Output**
Return the number of sawtooth subarrays.
Guaranteed constraints:
**2 ≤ arr.length ≤ 105,**
**-109 ≤ arr[i] ≤ 109.**
