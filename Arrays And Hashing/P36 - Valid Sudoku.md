# P36 - Valid Sudoku

| Link                                                | Tags           |
| --------------------------------------------------- | -------------- |
| [p36](https://leetcode.com/problems/valid-sudoku/) | #medium  #java |

## My Solution

| Runtime                                                            | Space                  |
| ------------------------------------------------------------------ | ---------------------- |
| $O(L * n \log n)$ where $L$ is the number of length of the `board`. | $O(3*n)$ due to 3 sets |


```java
import java.lang.Math;

class Solution {
    public boolean isValidSudoku(char[][] board) {
        
        // 'unique' sets
        Set<Character> digitsRow = new HashSet<>();
        Set<Character> digitsCol = new HashSet<>();

        // check rows
        for(int i = 0; i < board.length; i++){
            for (int j = 0; j < board.length; j++){
                // if seen two digits twice ret false
                if (board[i][j] != '.' &&  !digitsRow.add(board[i][j])){
                    return false;
                }
                if (board[j][i] != '.' &&  !digitsCol.add(board[j][i])){
                    return false;
                }
            }

            // flush old numbers
            digitsRow.clear();
            digitsCol.clear();
        }

        // check 3x3 boxes
        final int boxSize = (int) Math.sqrt(board.length);
        Set<Character> digits3x3 = new HashSet<>();


        // k, l index the 3x3 grids (idx = [0, 1, 2] X [0, 1, 2]) <- set Cartesian product
        for(int k = 0; k < board.length; k += boxSize){
            for(int l = 0; l < board.length; l += boxSize){
               
                 // internal box loop
                for(int m = k; m < k + boxSize; m++)
                    for (int n = l; n < l + boxSize; n++)
                        if(board[m][n] != '.' && !digits3x3.add(board[m][n]))
                            return false;
                            
                digits3x3.clear();
            }
        }
        
        return true;
    }
}
```

## Better Solution via `Strings`

The idea here is to encode locations and number in the same string to perform only one sweep and use only `Set`. 

```java
import java.lang.Math;

class Solution {
    public boolean isValidSudoku(char[][] board) {
    
        Set<String> locations = new HashSet();

        for(int row = 0; row < board.length; row++){
            for(int col = 0; col < board[0].length; col++){

                if(board[row][col] == '.') continue;

                int subBoxIndexRow = row / 3;
                int subBoxIndexCol = col / 3;

                String colLocation = String.format("(%d)%c", col, board[row][col]);
                String rowLocation = String.format("%c(%d)", board[row][col], row);
                String subLocation = String.format("(%d)(%d)%c", subBoxIndexRow, subBoxIndexCol, board[row][col]);

                if(!locations.add(rowLocation) || !locations.add(colLocation) || !locations.add(subLocation))
                    return false;
            }
        }
        return true;
    }
}
```

