# Arrays
* Set Zero Matrix - O(2*(n*m)) - O(1)

``` java
static void setZeroes(int[][] matrix) {
        int col0 = 1, rows = matrix.length, cols = matrix[0].length;

        for (int i = 0; i < rows; i++) {
            if (matrix[i][0] == 0) col0 = 0;
            for (int j = 1; j < cols; j++)
                if (matrix[i][j] == 0)
                    matrix[i][0] = matrix[0][j] = 0;
        }

        for (int i = rows - 1; i >= 0; i--) {
            for (int j = cols - 1; j >= 1; j--)
                if (matrix[i][0] == 0 || matrix[0][j] == 0)
                    matrix[i][j] = 0;
        if (col0 == 0) matrix[i][0] = 0;
        }
    }
```

* Pascal Triangle - O(n<sup>2</sup>) - O(n<sup>2</sup>)

```java
 public List<List<Integer>> generate(int numRows) {
         List<List<Integer>> list1 = new ArrayList<>();
        ArrayList<Integer> last = new ArrayList<>();
        for (int i = 0 ; i < numRows ; i++){
            ArrayList<Integer> inside = new ArrayList<>();
            for(int j = 0 ; j<=i ; j++){
                if(j==0 || j==i){
                    inside.add(j,1);
                }
                else{
                    inside.add(j,last.get(j) + last.get(j-1));
                }
            }
            last = inside;
            list1.add(i,inside);
        }
        return list1;
    }
}
```
