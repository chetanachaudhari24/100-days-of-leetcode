You are given an integer array cost where cost[i] is the cost of ith step on a staircase. Once you pay the cost, you can either climb one or two steps.
You can either start from the step with index 0, or the step with index 1.
Return the minimum cost to reach the top of the floor.

Example 1:

    Input: cost = [10,15,20]
    Output: 15
    Explanation: You will start at index 1.
    Pay 15 and climb two steps to reach the top.
    The total cost is 15.
Example 2:

    Input: cost = [1,100,1,1,1,100,1,1,100,1]
    Output: 6
    Explanation: You will start at index 0. 
    Pay 1 and climb two steps to reach index 2. 
    Pay 1 and climb two steps to reach index 4. 
    Pay 1 and climb two steps to reach index 6. 
    Pay 1 and climb one step to reach index 7.
    Pay 1 and climb two steps to reach index 9.
    Pay 1 and climb one step to reach the top.
    The total cost is 6.
Constraints:
    
    2 <= cost.length <= 1000
    0 <= cost[i] <= 999
Solution:

    class Solution {
    public int minCostClimbingStairs(int[] cost) {
    int[] sol = new int[cost.length];
    
            sol[0] = cost[0];
            if(cost.length>1)
                sol[1] = cost[1];
            
            for(int i=2;i<cost.length;i++){
                sol[i] = cost[i] + Math.min(sol[i-1], sol[i-2]);
            }
            
            return Math.min(sol[cost.length-1], sol[cost.length-2]);
        }
    }