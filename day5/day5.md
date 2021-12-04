# 5. 最长回文子串 2021-12-04

## java
```java
class Solution {
    public String longestPalindrome(String s) {
        int len = s.length();
        boolean[][] tp = new boolean[len][len];
        String res = "";

        for (int i = len - 1; i >= 0; i--) {
            for (int j = i; j < len; j++) {
                if (s.charAt(i) == s.charAt(j) && (j - i <= 1 || tp[i + 1][j - 1])) {
                    tp[i][j] = true;
                }
                if (tp[i][j] && (j - i + 1) > res.length()) {
                    res = s.substring(i, j + 1);
                }
            }
        }
        return res;
    }
}
````

## php
```php
class Solution {

    /**
     * @param String $s
     * @return String
     */
    function longestPalindrome($s) {
        $n = strlen($s);
        if ($n <= 1) return $s;
        $maxStart = 0; 
        $maxEnd = 0; 
        $maxLen = 0; 
        $dp = array_fill(0, $n, array_fill(0, $n, false));
        for ($i = 0; $i < $n; ++$i) {
            $dp[$i][$i] = true;
        }

        for ($r = 0; $r < $n; ++$r) {
            for ($l = 0; $l < $r; ++$l) {
                if ($s[$l] == $s[$r] && ($dp[$l + 1][$r - 1] || $r - $l < 2)) {
                    $dp[$l][$r] = true;
                    if ($r - $l + 1 > $maxLen) {
                        $maxLen = $r - $l + 1;
                        $maxStart = $l;
                        $maxEnd = $r;
                    }
                }
            }
        }

        return substr($s, $maxStart, $maxEnd - $maxStart + 1);
    }
}
```

## python
```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        res = ''
        for i in range(len(s)):
            s1 = self.find(s, i, i)       
            s2 = self.find(s, i, i+1)     
            
            if max(len(s1), len(s2)) > len(res):
                res = s2 if len(s1) < len(s2) else s1
        return res

    def find(self, s, left, right):
        while left >= 0 and right < len(s) and s[left] == s[right]:
            left -= 1
            right += 1
        return s[left+1:right]
````
