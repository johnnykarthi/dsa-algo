# 125. Valid Palindrome

A phrase is a **palindrome** if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string ``s``, return ``true`` if it is a ***palindrome***, or ``false`` otherwise.s

#### Example 1:

>**Input:** s = "A man, a plan, a canal: Panama"
>
>**Output:** true
>
>**Explanation:** "amanaplanacanalpanama" is a palindrome.


#### Example 2:

>**Input:** s = "race a car"
>
>**Output:** false
>
>**Explanation:** "raceacar" is not a palindrome.

#### Example 3:

>**Input:** s = " "
>
>**Output:** true
>
>**Explanation:** s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.

---

# Solutions

### *Optimized Solution*

```java

class Solution {
    public boolean isPalindrome(String s) {

        int i =0;
        int j = s.length()-1;
        
        while(i<j){
            if(Character.isLetterOrDigit(s.charAt(i)) && Character.isLetterOrDigit(s.charAt(j))){
                if(!(Character.toLowerCase(s.charAt(i)) == Character.toLowerCase(s.charAt(j)))) {
                    return false;
                }
                i++;
                j--;
            }
            if (!Character.isLetterOrDigit(s.charAt(i))) {
                i++;
            }
            if (!Character.isLetterOrDigit(s.charAt(j))) {
                j--;
            }
        }
        return true;
    }
}

```
