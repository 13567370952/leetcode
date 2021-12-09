# 6. Z 字形变换 2021-12-09

## java
```java
class Solution {
    public String convert(String s, int numRows) {
        if(numRows ==1 ) return s;
        List<StringBuilder> rows = new ArrayList<StringBuilder>();
        
        for(int i = 0; i < numRows; i++) 
            rows.add(new StringBuilder());
        int i = 0, flag = -1;
        for(char c : s.toCharArray()) {
            rows.get(i).append(c);
            if(i == 0 || i == numRows -1) flag = - flag;
            i += flag;
        }
        StringBuilder res = new StringBuilder();
        for(StringBuilder row : rows) res.append(row);
        return res.toString();
    }
}

````

## php
```php
class Solution {

    /**
     * @param String $s
     * @param Integer $numRows
     * @return String
     */
    function convert($s, $numRows) {
        if($numRows == 1){
            return $s;
        }
        $length = strlen($s);
        $arr = [];
        $i = 0;
        $flag = -1;
        for($len=0;$len<$length;$len++){
            $arr[$i] .=$s[$len];
            if($i==0 || $i%($numRows-1)==0){
                $flag = -$flag;
            }
            $i += $flag;
        }
        $new_s = implode("",$arr);
        return $new_s;
    }
}
```

## python
```python
class Solution:
    def convert(self, s: str, numRows: int) -> str:
        if numRows == 1:
            return s
        
        res = ["" for _ in range(numRows)]
        
        i, flag = 0, -1
        
        for c in s:
            res[i] += c
            if i == 0 or i == numRows - 1: flag = -flag
            i += flag
        
        return "".join(res)
````
