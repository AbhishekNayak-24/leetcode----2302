# leetcode----2302
Count Subarrays With Score Less than K
//code in java
class Solution {
    public long countSubarrays(int[] nums, long k) {
        long count = 0;
        long sum = 0;
        int left = 0;

        for (int right = 0; right < nums.length; right++) {
            sum += nums[right];

            // Shrink the window if the score is >= k
            while (sum * (right - left + 1) >= k) {
                sum -= nums[left];
                left++;
            }

            // All subarrays ending at 'right' and starting from 'left' are valid
            count += (right - left + 1);
        }

        return count;
    }
}
