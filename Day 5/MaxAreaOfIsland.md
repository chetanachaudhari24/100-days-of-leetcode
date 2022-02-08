You are given an m x n binary matrix grid. An island is a group of 1's (representing land) connected 4-directionally (horizontal or vertical.) You may assume all four edges of the grid are surrounded by water.
The area of an island is the number of cells with a value 1 in the island.
Return the maximum area of an island in grid. If there is no island, return 0.

Example 1:

    Input: grid = [[0,0,1,0,0,0,0,1,0,0,0,0,0],[0,0,0,0,0,0,0,1,1,1,0,0,0],[0,1,1,0,1,0,0,0,0,0,0,0,0],[0,1,0,0,1,1,0,0,1,0,1,0,0],[0,1,0,0,1,1,0,0,1,1,1,0,0],[0,0,0,0,0,0,0,0,0,0,1,0,0],[0,0,0,0,0,0,0,1,1,1,0,0,0],[0,0,0,0,0,0,0,1,1,0,0,0,0]]
    Output: 6
    Explanation: The answer is not 11, because the island must be connected 4-directionally.
Example 2:

    Input: grid = [[0,0,0,0,0,0,0,0]]
    Output: 0
Constraints:

    m == grid.length
    n == grid[i].length
    1 <= m, n <= 50
    grid[i][j] is either 0 or 1.

Solution:

    class Solution {
    int[][] grid;
    int [][] flag;
    
        public int maxAreaOfIsland(int[][] grid) {
            int max = 0;
            this.grid = grid;
            flag = new int[grid.length][grid[0].length];
            
            for(int i=0;i<grid.length;i++){
                for(int j=0;j<grid[0].length;j++){
                    max = Math.max(max, calculateArea(i, j));
                }
            }
            
            return max;
        }
        
        int calculateArea(int i, int j){
            
            if(i<0 || j<0 || i>=grid.length || j>=grid[0].length || flag[i][j]==1 || grid[i][j]==0)
                return 0;
            
            flag[i][j] = 1;
            
            return (1 + calculateArea(i+1, j)
                         + calculateArea(i-1, j)
                         + calculateArea(i, j+1)
                         + calculateArea(i, j-1));
                
        }
    }