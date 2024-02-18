## 0-1 KNAPSACK ALGORITHM

You are given N items that cannot be broken. Each item has a weight and value associated with it.
You also have a KnapSack of capacity W.
Find the maximum value of items you can collect in the KnapSack so that the total weight does not exceed W.

### Input

- First line contains the values N and W.
- Second line contains N integers denoting the weights.
- Last line contains N integers denoting the values.

### Output

Print the maximum value that can be collected with total weight less than or equal to W.

### Java

```import java.util.*;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int N = scanner.nextInt(); // Number of items
        int W = scanner.nextInt(); // Knapsack capacity
        int[] weights = new int[N]; // Array to store weights
        int[] values = new int[N];  // Array to store values
        
        // Input weights
        for (int i = 0; i < N; i++) {
            weights[i] = scanner.nextInt();
        }
        
        // Input values
        for (int i = 0; i < N; i++) {
            values[i] = scanner.nextInt();
        }
        
        // Create a 2D array to store maximum value for given weight capacity
        int[][] dp = new int[N + 1][W + 1];
        
        // Initialize dp array
        for (int i = 0; i <= N; i++) {
            for (int j = 0; j <= W; j++) {
                if (i == 0 || j == 0) {
                    dp[i][j] = 0;
                } else if (weights[i - 1] <= j) {
                    dp[i][j] = Math.max(values[i - 1] + dp[i - 1][j - weights[i - 1]], dp[i - 1][j]);
                } else {
                    dp[i][j] = dp[i - 1][j];
                }
            }
        }
        
        // Print the maximum value that can be collected
        System.out.println(dp[N][W]);
    }
}
```
