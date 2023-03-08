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
* Next permutations - O(N) -O(1)
``` java
class Solution {
    public void nextPermutation(int[] A) {
        if(A == null || A.length <= 1) return;
        int i = A.length - 2;
        while(i >= 0 && A[i] >= A[i + 1]) i--; 
        if(i >= 0) {                           
            int j = A.length - 1;              
            while(A[j] <= A[i]) j--;      
            swap(A, i, j);                     
        }
        reverse(A, i + 1, A.length - 1);      
}

public void swap(int[] A, int i, int j) {
    int tmp = A[i];
    A[i] = A[j];
    A[j] = tmp;
}

public void reverse(int[] A, int i, int j) {
    while(i < j) swap(A, i++, j--);
}
}
```
* Kadane's Algorithm(Maximum Subarray) - O(N) - O(1)
``` java
public static int maxSubArray(int[] nums,ArrayList<Integer> subarray) { 
        int msf=Integer.MIN_VALUE , meh=0 ; 
        int s=0;
        for(int i=0;i<nums.length;i++){ 
            meh+=nums[i]; 
            
            if(meh>msf)
            { 
                subarray.clear();
                msf=meh; 
                subarray.add(s); 
                subarray.add(i); 
            } 
            if(meh<0)
            {
                meh=0; 
                s=i+1;
                
            } 
        } 
 
        return msf; 
    } 
    public static void main(String args[])
    {
        int arr[]={-2,1,-3,4,-1,2,1,-5,4};
        ArrayList<Integer> subarray=new ArrayList<>();
        int lon=maxSubArray(arr,subarray);
        System.out.println("The longest subarray with maximum sum is "+lon);
        System.out.println("The subarray is ");
        for(int i=subarray.get(0);i<=subarray.get(1);i++)
        {
            System.out.print(arr[i]+" ");
        }
        
    }
}
```
