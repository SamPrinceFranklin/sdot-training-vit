## Edit Distance

Given two strings s1 and s2. Return the minimum number of operations required to convert s1 to s2. The possible operations are permitted:
- Insert a character at any position of the string.
- Remove any character from the string.
- Replace any character from the string with any other character.

**Input**  
Input consists of two lines, strings s1 and s2.

**Output**  
Print the minimum number of operations required to convert s1 to s2.


### Code Implementation

```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Prompt the user to enter the strings s1 and s2
        System.out.println("Enter the first string:");
        String s1 = scanner.nextLine();

        System.out.println("Enter the second string:");
        String s2 = scanner.nextLine();

        // Call the minDistance function and print the result
        int result = minDistance(s1, s2);
        System.out.println(result);
    }

    public static int minDistance(String word1, String word2) {
        int m = word1.length();
        int n = word2.length();

        int[][] dp = new int[m + 1][n + 1];

        // Initialize first row and column
        for (int i = 0; i <= m; i++)
            dp[i][0] = i;
        for (int j = 0; j <= n; j++)
            dp[0][j] = j;

        // Dynamic programming approach to fill the dp array
        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (word1.charAt(i - 1) == word2.charAt(j - 1))
                    dp[i][j] = dp[i - 1][j - 1];
                else
                    dp[i][j] = 1 + Math.min(dp[i - 1][j - 1], Math.min(dp[i][j - 1], dp[i - 1][j]));
            }
        }

        return dp[m][n];
    }
}
```
