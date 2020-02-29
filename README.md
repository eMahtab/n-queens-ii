# n-queens-ii
## https://leetcode.com/problems/n-queens-ii

# Implementation :

```java
class Solution {
    private int solution;
    public int totalNQueens(int n) {
        int[][] chessboard = new int[n][n];
        placeQueen(chessboard, 0);
        return solution;
    }
    
    private void placeQueen(int[][] chessboard, int colIndex) {
		if (colIndex == chessboard.length) {
            solution++;
		} else {
            for (int rowIndex = 0; rowIndex < chessboard.length; rowIndex++) {
                if (isPlaceValid(chessboard, rowIndex, colIndex)) {
                    chessboard[rowIndex][colIndex] = 1;
                    placeQueen(chessboard, colIndex+1);
                    chessboard[rowIndex][colIndex] = 0;
                }
		    }
        }
	}
    
    private boolean isPlaceValid(int[][] chessboard, int rowIndex, int colIndex) {
		for (int i = 0; i < colIndex; i++) {
			if (chessboard[rowIndex][i] == 1)
				return false;
        }
		for (int i = rowIndex, j = colIndex; i >= 0 && j >= 0; i--, j--) {
			if (chessboard[i][j] == 1)
				return false;
		}
		for (int i = rowIndex, j = colIndex; i < chessboard.length && j >= 0; i++, j--) {
			if (chessboard[i][j] == 1)
				return false;
		}
       return true;
	}
}
```

# References :
https://www.youtube.com/watch?v=FreUvSdLa_4
