(前面做过的一些数组和单链表的题目后续复习的时候再写进本文档)  
代码和思路主要参考以下地方 1、leetcode讨论区 2、https://github.com/wind-liang/leetcode
希望自己从以下几个方面对待题目  
#### 1. 刚开始思路
#### 2. 刚开始代码  
#### 3. 犯的错或者没想到的点  
#### 4. 新的思路  
#### 5. 新的代码  
#### 6. 总结及关联题目  

### 83. [Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)  
#### 1. 刚开始思路  
快慢指针，如果快慢指针不一样，则后移；（否则什么都不做）
#### 2. 刚开始代码  

```java
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        ListNode dummy=new ListNode(0);
        ListNode slow=dummy;
        while (head!=null){
            //System.out.println("slow:"+slow.val+"fast:"+head.val);
            if (head.val!=slow.val){
                slow.next=head;
                slow=head;
            }
            head=head.next;
        }
        //slow.next=null;  //漏写了这条
        return dummy.next;
    }
}
```
#### 3. 犯的错或者没想到的点  
> 快慢指针，如果快慢指针不一样，则后移；（否则什么都不做）  
什么都不做的话，对于最后一连串数字，如[1,1,2,3,3] 就会把最后两个3输出，没解链
#### 4. 新的思路  
把最后的慢指针所指位置指向空指针
#### 5. 新的代码  

```java
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        ListNode dummy=new ListNode(0);
        ListNode slow=dummy;
        while (head!=null){
            //System.out.println("slow:"+slow.val+"fast:"+head.val);
            if (head.val!=slow.val){
                slow.next=head;
                slow=head;
            }
            head=head.next;
        }
        slow.next=null;
        return dummy.next;
    }
}
```

#### 6. 总结及关联题目  
1、不要忘记把慢指针指向空  
2、递归的算法还没看


