# Ransom note problem
## Description - Checking whether a ransomNOte can be built using the magazine
### Approach
* Here, first we maintain a map for magazine Map<Character, Integer>. In the map we will be having the frequency of the character as a value
* Then, we loop through ransomNote and check whether the characters are in map and the frequency must be greater than zero
* We keep a count variable which we increment everytime when found the char in the map 
* Lastly we check whether ***count == ransomNote.length()***

```java
import java.util.Map;
import java.util.HashMap;
public class ransomNote {
    public static boolean canConstruct(String ransomNote, String magazine) {
        Map<Character, Integer> map = new HashMap<>();
        for(int i=0;i<magazine.length();i++) {
            char ch = magazine.charAt(i);
            if(map.containsKey(ch)) {
                map.put(ch, map.get(ch) + 1);
            } else {
                map.put(ch, 1);
            }
        }
        int count = 0;
        for(int i=0;i<ransomNote.length();i++) {
            char ch = ransomNote.charAt(i);
            if(map.containsKey(ch) && map.get(ch) > 0) {
                count++;
                map.put(ch, map.get(ch) - 1);
            } else {
                break;
            }
        }
        return count == ransomNote.length();
    }
    public static void main(String[] args) {
        System.out.println(canConstruct("bg", "efjbdfbdgfjhhaiigfhbaejahgfbbgbjagbddfgdiaigdadhcfcj"));
    }
}

```
