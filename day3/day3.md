# 3. 无重复字符的最长子串 2021-11-29

## java
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
          int r=0;
        int a[] = new int[128];
        int n  =s.length();
        for(int i=0,j=0,x=0; r<n-i ; a[x]=j){
            x = s.charAt(j);
            j++;
            if ( a[x] > i)
                i=a[x];
            if (j-i>r)
                r=j-i;
        }
        return r;
    }
}
````

## php
```php
class Solution {

    /**
     * @param String $s
     * @return Integer
     */
    function lengthOfLongestSubstring($s) {
        $a = [];
        for ($i = 0; $i < 128; $i++) {
            $a[$i] = -1;
        }
        $t = -1;
        $r = 0;
        $l = strlen($s);
        for ($i = 0; $i < $l; $i++) {
            $t = max($t, $a[$s[$i]]);
            $a[$s[$i]] = $i;
            $r = max($r, $i - $t);
        }
        return $r;
    }
}

```

## python
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        d={}
        index=0
        i=0
        r=0
        for i in range(len(s)):
            j=s[i]
            if j in d and d[j]>=index:
                index=d[j]+1
            else:
                r=max(r,i-index+1)
            d[j]=i
        return r
````
