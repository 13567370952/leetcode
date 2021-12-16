# 7. 整数反转 2021-12-16

## java
```java
class Solution {
    public int reverse(int x) {
        int res = 0;
        while (x != 0) {
            if (res > 214748364 || res < -214748364) {
                return 0;
            }
            res = res * 10 + x % 10;
            x = x / 10;
        }
        return res;
    }
}

````

## php
```php
class Solution {

    /**
     * @param Integer $x
     * @return Integer
     */
    function reverse($x) {
        $max = pow(2, 31);
        $s = intval(strrev(abs($x)));
        return $x>=0?($s+1>$max?0:$s):($s>$max?0:'-'.$s);
    }
}
```

## python
```python
class Solution:
    def reverse(self, x: int) -> int:
        y = int((str(abs(x)))[-1::-1])
        return y * (-1 if x < 0 else 1) if -2147483648 < y < 2147483647 else 0

````
