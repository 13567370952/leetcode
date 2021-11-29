# 2. 两数相加 2021-11-27

## java
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
         return addTwoNumbersDeep(l1,l2,0);
    }
    public ListNode addTwoNumbersDeep(ListNode l1, ListNode l2,int temp) {
        if(l1==null&&l2==null){return temp==0?null:new ListNode(temp);}
        if(l1 !=null){temp += l1.val;l1 = l1.next;}
        if(l2 !=null){temp += l2.val;l2 = l2.next;}
        return new ListNode(temp%10,addTwoNumbersDeep(l1,l2,temp/10));
    }
}
````

## php
```php
/**
 * Definition for a singly-linked list.
 * class ListNode {
 *     public $val = 0;
 *     public $next = null;
 *     function __construct($val = 0, $next = null) {
 *         $this->val = $val;
 *         $this->next = $next;
 *     }
 * }
 */
class Solution {

    /**
     * @param ListNode $l1
     * @param ListNode $l2
     * @return ListNode
     */
    function addTwoNumbers($l1, $l2) {
        return self::addTwoNumbersDeep($l1, $l2, 0);
    }

    function addTwoNumbersDeep($l1, $l2, $temp){
      if(empty($l1) && empty($l2)){return $temp == 0 ? null: new ListNode($temp);}
      if(!empty($l1)){$temp += $l1->val;$l1 = $l1->next;}
      if(!empty($l2)){$temp += $l2->val;$l2 = $l2->next;}
      return new ListNode($temp%10, self::addTwoNumbersDeep($l1, $l2, $temp>=10 ? 1:0));
    }
    
}

```

## python
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        def addTwoNumbersDeep(l1, l2, i):
            if not l1 and not l2 and not i: return None
            s = (l1.val if l1 else 0) + (l2.val if l2 else 0) + i
            node = ListNode(s % 10)
            node.next = addTwoNumbersDeep(l1.next if l1 else None, l2.next if l2 else None, s // 10)
            return node
        return addTwoNumbersDeep(l1, l2, 0)
````
