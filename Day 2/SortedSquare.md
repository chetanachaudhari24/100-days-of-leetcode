Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.

Example 1:

Input: nums = [-4,-1,0,3,10]
Output: [0,1,9,16,100]
Explanation: After squaring, the array becomes [16,1,0,9,100].
After sorting, it becomes [0,1,9,16,100].
Example 2:

Input: nums = [-7,-3,2,3,11]
Output: [4,9,9,49,121]


Constraints:

1 <= nums.length <= 104
-104 <= nums[i] <= 104
nums is sorted in non-decreasing order.

    class Solution {
    public int[] sortedSquares(int[] nums) {
    int start = 0;
    int end = nums.length -1;
    int[] sol= new int[nums.length];
    int i=nums.length-1;
    
            while(start<=end){
                
                if(Math.abs(nums[start])<Math.abs(nums[end])){
                    sol[i] = nums[end]*nums[end];
                    end--;
                }
                else{
                    sol[i] = nums[start]*nums[start];
                    start++;
                }
                
                i--;
            }
            
            return sol;
            
        }
    }