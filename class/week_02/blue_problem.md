### ICI #1: String Manipulation - BLUE
___
#### Blue Problem
Given an input string, reverse the string word by word.

#### Assumptions
- The string will not be null
- The string could be the empty string

*Target:* Please describe an O(n) solution for this problem.

#### Examples

Let us call the function that does this `reverseWords(s)`. Consider the following examples:

```java
reverseWords("the sky is blue") // "blue is sky the"
reverseWords(" 1") // "1"
```

____

#### Solution

The initial way we could do this is to create an array of all of the words using the `String.split` function, and then add words backwards to a return string. `String.split` takes a string, and splits it on a given substring. For examples, `"Hello world".split(" ")` would return `["Hello", "world"]`. We iterate backwards, adding the words and then spaces to the list (we must remove the last space).

```java
public String reverseWords(String s) {
    String[] words = s.split(" ");
    String ret = "";
    for (int i = words.length - 1; i >= 0; i -= 1) {
        /*
        We need this check because if we call split on " 1", it would return the array ["", "1"], and we do not want to add "" followed by a space.
         */
        if (!words[i].equals("")) {
            ret += words[i] + " ";
        }
    }   
    /*
    This is a ternary operator.
    What we have written is equivalent to:
        if (!ret.equals("")) {
            return ret.substring(0, ret.length() - 1);
        } else { 
            return "";
        }
     */
    return !ret.equals("") ? ret.substring(0, ret.length() - 1) : "";
}
```

This solution is valid, but we should think about Java and how Strings are implemented. Strings are immuatable in Java, which means that every string you create is put into memory and cannot be changed. This means that every time we update our return string, it creates a new string in memory. Even though this is O(n), that means our space complexity could be reduced. Let us take a look at the implementation of this function with the use of `StringBuilder`. `StringBuilder` is a class designed to be an accumulator to create Strings, but will not actually create a String until you call `toString()` on it.

```java
public String reverseWords(String s) {
    String[] words = s.split(" ");
    StringBuilder sb = new StringBuilder();
    for (int index = words.length - 1; index >= 0; index -= 1) {
        if (!words[index].equals("")) {
            sb.append(words[index]);
            sb.append(' ');
        }
    }
    if (sb.length() > 0 && sb.charAt(sb.length() - 1) == ' ') {
        sb.deleteCharAt(sb.length() - 1);
    }
    return sb.toString();
}
```

[Source](https://leetcode.com/problems/reverse-words-in-a-string/description/)