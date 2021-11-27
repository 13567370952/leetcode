# 1、两数之和 2021-11-27

## java
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
       Map<Integer, Integer> map = new HashMap<>();
       for (int i = 0; i < nums.length; i++) {
            if (map.containsKey(target - nums[i])) {
            	//存在则返回相应序号
            return new int[] { map.get(target - nums[i]), i };
            }
            map.put(nums[i], i);
        }
    return null;
    }
}

````

## php
```php
class Solution {

    /**
     * @param Integer[] $nums
     * @param Integer $target
     * @return Integer[]
     */
    function twoSum($nums, $target) {
        for ($i=0; $i< count($nums); $i++){
             $r = $target - $nums[$i];
             $match_index = array_search($r, $nums);
            if ($match_index !== false && $match_index != $i) {
                return array($i, $match_index);
            }
        }
        return [];
    }
}

```

## python
```python
#第一种遍历
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        r = {}
        for i in nums:
            if target - i not in r:
                r[i] = nums.index(i)
            else:
                return [r[target - i],  nums.index(i)]
#第二种遍历
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        r = {}
        for i in range(len(nums)):
            if target - nums[i] not in r:
                r[nums[i]] = i
            else:
                return [r[target - nums[i]],  i]
#第三种遍历
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        r = {}
        for i, v in enumerate(nums):
            if target - v not in r:
                r[v] = i
            else:
                return [r[target - v], i]
````
