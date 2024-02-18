## Wildcard Pattern Matching

You are given a pattern string containing letters and wildcard characters. The wildcard character * can match any sequence of characters (including an empty sequence), and the wildcard character ? can match any single character. Your task is to implement a function that determines whether a given input string matches the provided pattern. Return true if the pattern can be equated to the text otherwise, false.

Here are the rules for wildcard matching:
- The wildcard character * can match any sequence of characters (including an empty sequence).
- The wildcard character ? can match any single character.

**Write a function `isMatch(pattern: str, input_str: str) -> bool` that returns True if the input string matches the pattern, and False otherwise.**

### Input
The input must be in Two lines.
1st Line, Enter the Text.
2nd Line, Enter the Wildcard Pattern.

### Output
Return true if the pattern can be equated to the text otherwise, false.



### Code Implementation

```java
import java.util.*;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        // Prompt the user to enter the text
        System.out.println("Enter the Text:");
        String text = scanner.nextLine();
        
        // Prompt the user to enter the wildcard pattern
        System.out.println("Enter the Wildcard Pattern:");
        String pattern = scanner.nextLine();
        
        // Call the isMatch function and print the result
        boolean result = isMatch(pattern, text);
        System.out.println(result);
    }

    public static boolean isMatch(String pattern, String input_str) {
        // Initialize pointers for pattern and input string
        int p = 0, s = 0;
        // Initialize pointers to record the positions of '*' and last '*' in the pattern
        int starIndex = -1, sTmp = -1;
        // Iterate through the input string
        while (s < input_str.length()) {
            // If pattern and input string match or pattern has '?', move both pointers
            if (p < pattern.length() && (pattern.charAt(p) == '?' || pattern.charAt(p) == input_str.charAt(s))) {
                p++;
                s++;
            }
            // If pattern has '*', record the position of '*' in pattern and the current position in input string
            else if (p < pattern.length() && pattern.charAt(p) == '*') {
                starIndex = p;
                sTmp = s;
                p++;
            }
            // If current characters don't match and there's no '*', backtrack
            else if (starIndex != -1) {
                // Backtrack to the position of '*' in pattern and move the input string pointer to the next position
                p = starIndex + 1;
                s = ++sTmp;
            }
            // If no '*' found and characters don't match, return false
            else {
                return false;
            }
        }
        // Skip any consecutive '*' in the pattern
        while (p < pattern.length() && pattern.charAt(p) == '*') {
            p++;
        }
        // If pattern pointer reached the end, return true, otherwise false
        return p == pattern.length();
    }
}
```
