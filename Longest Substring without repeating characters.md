### Question:
You are given a string `s`. Your task is to find the length of the longest substring that contains each character at most once. A substring is a contiguous sequence of characters within a string.

Write a function `longestSubstringLength` to solve this problem.

### Input Format:
Enter the string `s` without any spaces.

### Output Format:
Return the length of the longest substring as an integer.


### Code (Java):

```java
import java.util.*;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String s = scanner.next();
        System.out.println(longestSubstringLength(s));
    }

    public static int longestSubstringLength(String s) {
        int n = s.length();
        Map<Character, Integer> seen = new HashMap<>();
        int start = 0;
        int maxLength = 0;

        for (int end = 0; end < n; end++) {
            char currentChar = s.charAt(end);
            if (seen.containsKey(currentChar)) {
                start = Math.max(start, seen.get(currentChar) + 1);
            }
            seen.put(currentChar, end);
            maxLength = Math.max(maxLength, end - start + 1);
        }

        return maxLength;
    }
}
```
