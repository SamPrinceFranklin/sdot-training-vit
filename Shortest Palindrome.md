### Question - Shortest Palindrome:
Given a string, find the shortest palindrome that can be obtained by adding characters in front of it.

### Input Format:
Enter the string without any spaces.

### Output Format:
Print the shortest palindrome as a string.

import java.util.*;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String s = scanner.next();
        System.out.println(shortestPalindrome(s));
    }

    public static String shortestPalindrome(String s) {
        int n = s.length();
        int i = 0;
        for (int j = n - 1; j >= 0; j--) {
            if (s.charAt(i) == s.charAt(j)) {
                i++;
            }
        }
        if (i == n) {
            return s; // The string is already a palindrome
        }
        String suffix = s.substring(i);
        String prefix = new StringBuilder(suffix).reverse().toString();
        String mid = shortestPalindrome(s.substring(0, i));
        return prefix + mid + suffix;
    }
}
```
