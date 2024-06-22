# LEETCODE-Array-1248
Let's perform a dry run of the `numberOfSubarrays` method with a sample input to understand how it works. Here, we'll use the example input `nums = [1, 1, 2, 1, 1]` and `k = 3`.

### Method Explanation
The method `numberOfSubarrays` calculates the number of subarrays with exactly `k` odd numbers by finding the difference between the number of subarrays with at most `k` odd numbers and the number of subarrays with at most `k-1` odd numbers.

### `numberOfSubarraysAtMost`
The helper method `numberOfSubarraysAtMost` computes the number of subarrays with at most `k` odd numbers. It uses a sliding window approach with two pointers `l` (left) and `r` (right).

### Step-by-Step Dry Run
1. **Initialization**
   - `numberOfSubarrays(nums = [1, 1, 2, 1, 1], k = 3)`
   - Calls `numberOfSubarraysAtMost(nums, 3)` and `numberOfSubarraysAtMost(nums, 2)`
   
2. **numberOfSubarraysAtMost(nums, 3)**
   - `ans = 0`, `l = 0`, `r = 0`, `k = 3`
   - Iterate through `r`:
     - `r = 0`: `nums[0] = 1` (odd), `--k = 2`
       - `ans += r - l = 0`
       - `r = 1`
     - `r = 1`: `nums[1] = 1` (odd), `--k = 1`
       - `ans += r - l = 1`
       - `r = 2`
     - `r = 2`: `nums[2] = 2` (even)
       - `ans += r - l = 3`
       - `r = 3`
     - `r = 3`: `nums[3] = 1` (odd), `--k = 0`
       - `ans += r - l = 6`
       - `r = 4`
     - `r = 4`: `nums[4] = 1` (odd), `--k = -1`
       - `ans += r - l = 10`
       - `l = 1`, `nums[0] = 1` (odd), `++k = 0`
       - `ans += r - l = 13`
       - `r = 5`
     - End of loop (since `r > nums.length`), returns `ans = 13`
   
3. **numberOfSubarraysAtMost(nums, 2)**
   - `ans = 0`, `l = 0`, `r = 0`, `k = 2`
   - Iterate through `r`:
     - `r = 0`: `nums[0] = 1` (odd), `--k = 1`
       - `ans += r - l = 0`
       - `r = 1`
     - `r = 1`: `nums[1] = 1` (odd), `--k = 0`
       - `ans += r - l = 1`
       - `r = 2`
     - `r = 2`: `nums[2] = 2` (even)
       - `ans += r - l = 3`
       - `r = 3`
     - `r = 3`: `nums[3] = 1` (odd), `--k = -1`
       - `ans += r - l = 6`
       - `l = 1`, `nums[0] = 1` (odd), `++k = 0`
       - `ans += r - l = 8`
       - `r = 4`
     - `r = 4`: `nums[4] = 1` (odd), `--k = -1`
       - `ans += r - l = 11`
       - `l = 2`, `nums[1] = 1` (odd), `++k = 0`
       - `ans += r - l = 13`
       - `r = 5`
     - End of loop (since `r > nums.length`), returns `ans = 13`

4. **Final Calculation**
   - `numberOfSubarrays(nums, 3) = 13 - 8 = 5`

### Conclusion
The method correctly calculates the number of subarrays with exactly 3 odd numbers in the given array `nums = [1, 1, 2, 1, 1]`, which is `5`. 

This example demonstrates the logic behind the sliding window approach and how it counts the subarrays with at most `k` odd numbers. The subtraction of results from two different `k` values gives the exact count for subarrays with exactly `k` odd numbers.
