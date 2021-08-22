# 36. Valid Sudoku

![](.gitbook/assets/image%20%2820%29.png)

![red , i index , i th row. Blue , j index, j th col  ](.gitbook/assets/inkedimage_li%20%282%29.jpg)

#### example 1.

```text
Input: board = 
[["5","3",".",".","7",".",".",".","."]
,["6",".",".","1","9","5",".",".","."]
,[".","9","8",".",".",".",".","6","."]
,["8",".",".",".","6",".",".",".","3"]
,["4",".",".","8",".","3",".",".","1"]
,["7",".",".",".","2",".",".",".","6"]
,[".","6",".",".",".",".","2","8","."]
,[".",".",".","4","1","9",".",".","5"]
,[".",".",".",".","8",".",".","7","9"]]
Output: true
```

#### THINK

1. use HashMap ,array of row , col and box to save the number , count pair.
2. row\[i\] represent , the **i-th row** of sudoku, col\[j\] represent **j-th col**.
3. box Index is defined by i \(vertical increase index\) , and j \(horizontal\) i/3 + \(j/3\) \* 3
4. loop all cell in the sudoku , and save in HashMap or array.

#### STEPS

1. create array for row, col and box
2. every row with curNum has only 1 count, so , **row\[i\]\[num\] = 1 \(i-th row num 出現次數=1\)**
3. col has same condition. col\[j\]\[num\] = 1
4. for loop every board cell. and minus '1'
5. nth box is n = i/3 + j/3\*3

```javascript
    public boolean isValidSudoku(char[][] board) {
        int [][] row = new int[9][9];
        int [][] col = new int[9][9];
        int [][] box = new int[9][9];
        for(int i = 0 ; i < board.length; i++){
            for(int j = 0 ; j < board[0].length ; j++){
                int curNum = board[i][j];
                if(curNum != '.'){
                    curNum = curNum - '1' ; // - '1' ,
                                            // 1 的ascii 49 - 49 = 0, 
                                            // 2's ascii 50 -29 = 1, 
                                            // 剛好對應array index 0-8
                    int boxIndex = i/3 + j/3 * 3;
                    if(row[i][curNum] == 1) {
                        return false;  
                    }else{
                        row[i][curNum] = 1;
                    }
                    
                    if(col[j][curNum] == 1){
                        return false;
                    }else{
                        col[j][curNum] = 1;
                    }
                    
                    if(box[boxIndex][curNum] == 1){
                        return false;
                    }else {
                       box[boxIndex][curNum] = 1; 
                    }
                }
            }
        }
        return true;
    }
```

