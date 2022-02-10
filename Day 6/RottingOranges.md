You are given an m x n grid where each cell can have one of three values:

0 representing an empty cell,
1 representing a fresh orange, or
2 representing a rotten orange.
Every minute, any fresh orange that is 4-directionally adjacent to a rotten orange becomes rotten.

Return the minimum number of minutes that must elapse until no cell has a fresh orange. If this is impossible, return -1.

Example 1:

    Input: grid = [[2,1,1],[1,1,0],[0,1,1]]
    Output: 4
Example 2:

    Input: grid = [[2,1,1],[0,1,1],[1,0,1]]
    Output: -1
    Explanation: The orange in the bottom left corner (row 2, column 0) is never rotten, because rotting only happens 4-directionally.
Example 3:
    
    Input: grid = [[0,2]]
    Output: 0
    Explanation: Since there are already no fresh oranges at minute 0, the answer is just 0.

Solution:

    class Solution {
    public int orangesRotting(int[][] grid) {
    int m = grid.length;
    int n = grid[0].length;
    int min =2;
    
            for(int i=0;i<m;i++){
                for(int j=0;j<n;j++){
                    if(grid[i][j]==2)
                        rotting(grid, i,j,2);
                }
            }
            
            for(int i=0;i<m;i++){
                for(int j=0;j<n;j++){
                    if(grid[i][j]==1)
                        return -1;
                    min = Math.max(min, grid[i][j]);
                    
                }
            }
            
            return min-2;
            
        }
         
        public void rotting(int[][] grid, int i, int j, int min){
            if(i<0 || j<0 || i>=grid.length || j>=grid[0].length || grid[i][j]==0 || (1 < grid[i][j] && grid[i][j] < min))
                return;
            else{
                grid[i][j] = min;
                rotting(grid, i+1, j, min+1);
                rotting(grid, i-1, j, min+1);
                rotting(grid, i, j+1, min+1);
                rotting(grid, i, j-1, min+1);
            }
        }
    }