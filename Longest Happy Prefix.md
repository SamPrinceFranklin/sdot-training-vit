### Question:
Given a string `s`, find and return the longest happy prefix. A string is called a happy prefix if it is a non-empty prefix which is also a suffix (excluding itself). If no such prefix exists, return an empty string.

Write a function `longestHappyPrefix` to solve this problem.


### Code (Java):

```java
import java.util.*;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String s = scanner.next();
        System.out.println(longestHappyPrefix(s));
    }

    public static String longestHappyPrefix(String s) {
        int n = s.length();
        int[] lps = new int[n];
        int len = 0;
        int i = 1;

        while (i < n) {
            if (s.charAt(i) == s.charAt(len)) {
                len++;
                lps[i] = len;
                i++;
            } else {
                if (len != 0) {
                    len = lps[len - 1];
                } else {
                    lps[i] = 0;
                    i++;
                }
            }
        }

        int prefixSuffixLength = lps[n - 1];
        return s.substring(0, prefixSuffixLength);
    }
}
```
