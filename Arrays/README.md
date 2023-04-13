.. contents::
   :local:
   :depth: 3

# Arrays
* Set Zero Matrix - O(2*(n*m)) - O(1)

.. code:: c++
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
* Stock and buy - O(N) - O(1)
```  java
    static int maxProfit(int[] arr) {
    int maxPro = 0;
    int minPrice = Integer.MAX_VALUE;
    for (int i = 0; i < arr.length; i++) {
      minPrice = Math.min(minPrice, arr[i]);
      maxPro = Math.max(maxPro, arr[i] - minPrice);
    }
    return maxPro;
  }
}
```
* Rotate Matrix -O(N*N) + O(N*N) - O(1)
``` java
import java.util.*;
class TUF {
    static void rotate(int[][] matrix) {
        for (int i = 0; i < matrix.length; i++) {
            for (int j = i; j < matrix[0].length; j++) {
                int temp = 0;
                temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix.length / 2; j++) {
                int temp = 0;
                temp = matrix[i][j];
                matrix[i][j] = matrix[i][matrix.length - 1 - j];
                matrix[i][matrix.length - 1 - j] = temp;
            }
        }
    }

    public static void main(String args[]) {
        int arr[][] =  {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
        rotate(arr);
        System.out.println("Rotated Image");
        for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j < arr.length; j++) {
                System.out.print(arr[i][j] + " ");
            }
            System.out.println();
        }

    }
}
```
* Merge two sorted array without extra space - O(N*M) - O(1)
``` java
static void merge(int[] arr1, int arr2[], int n, int m) {
    // code here
    int i, k;
    for (i = 0; i < n; i++) {
      // take first element from arr1 
      // compare it with first element of second array
      // if condition match, then swap
      if (arr1[i] > arr2[0]) {
        int temp = arr1[i];
        arr1[i] = arr2[0];
        arr2[0] = temp;
      }

      // then sort the second array
      // put the element in its correct position
      // so that next cycle can swap elements correctly
      int first = arr2[0];
      // insertion sort is used here
      for (k = 1; k < m && arr2[k] < first; k++) {
        arr2[k - 1] = arr2[k];
      }
      arr2[k - 1] = first;
    }
  }
}
```
* Find duplicate in an array - O(N)-O(1)
``` java
class TUF {
    public static int findDuplicate(int[] nums) {
        int slow = nums[0];
        int fast = nums[0];
        do {
            slow = nums[slow];
            fast = nums[nums[fast]];
        } while (slow != fast);

        fast = nums[0];
        while (slow != fast) {
            slow = nums[slow];
            fast = nums[fast];
        }
        return slow;
    }
    public static void main(String args[]) {
        int arr[] = {1,3,4,2,3};
        System.out.println("The duplicate element is " + findDuplicate(arr));
    }
}
```
* Find Repeating number and missing number - O(N) - O(1)
``` java
static ArrayList<Integer> missing_repeated_number(List<Integer> A) {
        long len = A.size();

        long S = (len * (len + 1) ) / 2;
        long P = (len * (len + 1) * (2 * len + 1) ) / 6;
        long missingNumber = 0, repeating = 0;

        for (int i = 0; i < A.size(); i++) {
            S -= (long)A.get(i);
            P -= (long)A.get(i) * (long)A.get(i);
        }

        missingNumber = (S + P / S) / 2;

        repeating = missingNumber - S;

        ArrayList<Integer> ans = new ArrayList<>();

        ans.add((int)repeating);
        ans.add((int)missingNumber);

        return ans;
    }
```
* Search in sorted matrix - O(nlog(n*m)) - O(1)
``` java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int lo = 0;
        if(matrix.length == 0) return false;
        int n = matrix.length; 
        int m = matrix[0].length; 
        int hi = (n * m) - 1;
        
        while(lo <= hi) {
            int mid = (lo + (hi - lo) / 2);
            if(matrix[mid/m][mid % m] == target) {
                return true;
            }
            if(matrix[mid/m][mid % m] < target) {
                lo = mid + 1;
            }
            else {
                hi = mid - 1;
            }
        }
        return false;
    }
}
```
* power(X,n) - O(nlogn) - O(1)
``` java
import java.util.*;
 public class Main{
 public static double myPow(double x, int n) {
    double ans = 1.0;
    long nn = n;
    if (nn < 0) nn = -1 * nn;
    while (nn > 0) {
      if (nn % 2 == 1) {
        ans = ans * x;
        nn = nn - 1;
      } else {
        x = x * x;
        nn = nn / 2;
      }
    }
    if (n < 0) ans = (double)(1.0) / (double)(ans);
    return ans;
  }

    public static void main(String args[])
    {
        System.out.println(myPow(2,10));
    }
 }
 ```
* Find the Majority Element that occurs more than N/2 times - O(N) - O(1)
``` java
class Solution {
    public int majorityElement(int[] nums) {
        int count = 0;
        int element = 0;

        for(int i=0;i<nums.length;i++){
            if(count==0) element = nums[i];
            if(nums[i]==element){
                count++;
            }else
                count--;
        }
        return element;
        
    }
}
```
* Find the Majority Element that occurs more than N/3 times - O(N) - O(1)
``` java
public static ArrayList < Integer > majorityElement(int[] nums) {

    int number1 = -1, number2 = -1, count1 = 0, count2 = 0, len = nums.length;
    for (int i = 0; i < len; i++) {
      if (nums[i] == number1)
        count1++;
      else if (nums[i] == number2)
        count2++;
      else if (count1 == 0) {
        number1 = nums[i];
        count1 = 1;
      } else if (count2 == 0) {
        number2 = nums[i];
        count2 = 1;
      } else {
        count1--;
        count2--;
      }
    }
    ArrayList < Integer > ans = new ArrayList < Integer > ();
    count1 = 0;
    count2 = 0;
    for (int i = 0; i < len; i++) {
      if (nums[i] == number1)
        count1++;
      else if (nums[i] == number2)
        count2++;
    }
    if (count1 > len / 3)
      ans.add(number1);
    if (count2 > len / 3)
      ans.add(number2);
    return ans;
  }
  ```
  * Grid Unique Paths - O(N-1) - O(1)
  ``` java
  class Solution {
    public int uniquePaths(int m, int n) {
        int N = m+n-2;
        int r = m-1;
        double res =1;
        for(int i=1;i<=r;i++){
            res = res*(N-r+i)/i;

        }
        return (int)res;
        
    }
}
```



