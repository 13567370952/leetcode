# 4. 寻找两个正序数组的中位数 2021-11-30

## java
```java
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int[] tempNums =  new int[nums1.length + nums2.length];
        System.arraycopy(nums1,0,tempNums,0,nums1.length);
        System.arraycopy(nums2,0,tempNums,nums1.length,nums2.length);
        Arrays.sort(tempNums);
        double res = 0;
        if(tempNums.length % 2 != 1){
            res = (tempNums[(tempNums.length)/2 -1] + tempNums[(tempNums.length)/2])/2.0;
        }else {
            res =  tempNums[(tempNums.length-1)/2];
        }
        return res;
    }
}
````

## php
```php
class Solution {

    /**
     * @param Integer[] $nums1
     * @param Integer[] $nums2
     * @return Float
     */
    function findMedianSortedArrays($nums1, $nums2) {
        $temp = array_merge($nums1 , $nums2);
        sort($temp);
        if(count($temp)%2){
            return $temp[(count($temp)-1)/2];
        }else{
            return ( $temp[count($temp)/2] + $temp[(count($temp)/2)-1] ) / 2;
        }
    }
}

```

## python
```python
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        temp = sorted(nums1 + nums2)
        temp_len = len(temp)
        if temp_len % 2 :
            return temp[temp_len // 2]
        else:
            return (temp[temp_len // 2 - 1] + temp[temp_len // 2]) / 2
````
