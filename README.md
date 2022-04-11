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

```sh
def solution(inputArray):
    if len(inputArray) in [0, 1]:
        return 0
    if len(inputArray) == 2 and (
            inputArray[0] > inputArray[1] or inputArray[1] > inputArray[0]):
        return 1
    sawCount = 0
    for i in range(len(inputArray)):
        prev = inputArray[i]
        pattern = "-"
        for j in range(i + 1, len(inputArray)):
            if inputArray[j] > prev and pattern in ["-", "down"]:
                sawCount += 1
                pattern = "up"

            elif inputArray[j] < prev and pattern in ["-", "up"]:
                sawCount += 1
                pattern = "down"
            else:
                break
            prev = inputArray[j]
    return sawCount

print(solution([1, 2, 1, 2, 1]))
print(solution([-14, -10, -20, -8, -10, 3, 2, 5, 5, 4, 6, 2, 3]))
print(solution([9, 8, 7, 6, 5]))
print(solution([-14, -10, -20, -8, -10, 3, 2, 5, 5, 4]))


```

[O(n)](https://vigges.net/qa/?qa=115994/) 
```sh
function sawSequenceImprove(number) {
    // best case
    if (number.length === 0 || number.length === 1) {
        return 0
    }
    
    if (number.length === 2 && ( number[0] > number[1] || number[1] > number[0])) {
        return 1
    }
    
    let sawCount = 0;
    if (number[0] > number[1] || number[1] > number[0]) {
        sawCount = 1;
    }
    let count = 0;
    let isLastConsArr = false;
    let startIndex = 0;
    for (let i = 2; i < number.length; i++) {
      // check sequence / and /
      if (
          (i - 2) >= 0 && 
          ((number[i - 2] < number[i - 1] && number[i - 1] > number[i]) ||
          (number[i - 2] > number[i - 1] && number[i - 1] < number[i]))
        ) {
        count += (2 + startIndex);
        const isDown = number[i - 1] > number[i];
        //checking last condition
        if (number[i] === number[i + 1] || 
            (isDown && number[i] > number[i+1]) || 
            (!isDown && number[i] < number[i+1]) || 
            (i + 1 === number.length)) {
            isLastConsArr = true
        }
        startIndex += 1
      }
      else if (number[i - 1] > number[i] || number[i - 1] < number[i]) {
          sawCount += 1
          count = 0
      }
      
      if (isLastConsArr) {
        sawCount += count
        isLastConsArr = false
        startIndex = 0
      }
    }
    return sawCount
}
console.log(sawSequenceImprove([-14, -10, -20, -8, -10, 3, 2, 5, 5, 4, 6, 2, 3]))
console.log(sawSequenceImprove([1, 2, 1, 3, 2]))
console.log(sawSequenceImprove([9, 8, 7, 6, 5]))
console.log(sawSequenceImprove([-14, -10, -20, -8, -10, 3, 2, 5, 5, 4]))
```
