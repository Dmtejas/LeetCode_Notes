# Finding the first unique character in a given string

Given a string s, find the first non-repeating character in it and return its index. If it does not exist, return -1.

 

Example 1:

Input: s = "leetcode"

Output: 0

Explanation:

The character 'l' at index 0 is the first character that does not occur at any other index.

### My Approach : 
* Createa Map of Character, Integer but not with HashMap<>() but with LinkedHashMap<>() it keeps track of the insertion order which is exactly what we need

* Then loop over the map using keySet() function and checks for the first char in the map which has value of 1 and put it in string.indexOf() and return the value 

* Otherwise, Return -1 as there are no unique elements

* Time Complexity - O(N)

```java
import java.util.*;

public class UniqueCharacter {
    public static int firstUniqueChar(String s) {
        Map<Character, Integer> map = new LinkedHashMap<>();
        for(int i=0;i<s.length();i++) {
            char ch = s.charAt(i);
            if(map.containsKey(ch)) {
                map.put(ch, map.get(ch) + 1);
            } else {
                map.put(ch, 1);
            }
        }
//        Set<Character> set = new HashSet<>();
//        set = map.keySet();
//        List<Character> list = new ArrayList<>();
        System.out.println(map);
        for(char key : map.keySet()) {
            if(map.get(key) == 1) {
                return s.indexOf(key);
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        System.out.println(firstUniqueChar("loveleetcode"));
    }
}

```

### Optimal Approach - Developer Docs
* Here, The same Map approach is followed but this time it is the HashMap<>() after that we loop through the given string and find out the first character having value 1 in HashMap<>()

```java
public class FirstUniqueChar {
    public static int firstUniqChar(String s)  {
        Map<Character, Integer> map = new HashMap<>();
        for(int i=0;i<s.length();i++) {
            char ch = s.charAt(i);
            if(map.containsKey(ch)) {
                map.put(ch, map.get(ch) + 1);
            } else {
                map.put(ch, 1);
            }
        }

        for(int i=0;i<s.length();i++) {
            char ch = s.charAt(i);
            if(map.get(ch) == 1) {
                return i;
            }
        }
        return -1;
    }
}
```
