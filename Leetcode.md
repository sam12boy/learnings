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

### [82. Remove Duplicates from Sorted List II](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/)   
#### 1. 刚开始思路  
刚开始我想，如果要在遍历的过程中，保证重复数不在结果中出现，就是要使 head.val!=head.next.val && head.next.val!= head.next.next.val  
但是考虑到上面next.next触及的边界情况多了点，要是一个next还能拉出来讨论，于是想到从head开始  prev.val!=head.val && head.val!=head.next.val  
#### 2. 刚开始代码  
```java
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        ListNode dummy=new ListNode(-999);
        ListNode slow=dummy,prev=dummy;
        while(head!=null){
            if (head.next==null){
                if (prev.val!=head.val){
                    slow.next=head;
                }
                else{
                    slow.next=null;
                }
                break;
            }
            System.out.println("slow:"+slow.val+" prev:"+prev.val+" head:"+head.val);
            if (head.val!=prev.val && head.val!=head.next.val){   //head.next到null的情况单独讨论
                slow.next=head;
                slow=head;
                prev=head;   //这一步应该是公共的
            }
            head=head.next;
        }
        return dummy.next;
    }
}
```
#### 3. 犯的错或者没想到的点  
prev指针应该跟着head一起移动  
#### 4. 新的思路  
#### 5. 新的代码  
```java
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        ListNode dummy=new ListNode(-999);
        ListNode slow=dummy,prev=dummy;
        while(head!=null){
            if (head.next==null){
                if (prev.val!=head.val){
                    slow.next=head;
                }
                else{
                    slow.next=null;
                }
                break;
            }
            //System.out.println("slow:"+slow.val+" prev:"+prev.val+" head:"+head.val);
            if (head.val!=prev.val && head.val!=head.next.val){   //head.next到null的情况单独讨论
                slow.next=head;
                slow=head;
            }
            prev=head;
            head=head.next;
        }
        return dummy.next;
    }
}
```
#### 6. 总结及关联题目  
1、有空可以看下wind-liang页面这个解法，他比我少用了一个指针记录当前不重复数字（还是说比我少个prev指针，反正就是少个指针）  
2、有空看下递归解

### [61. Rotate List](https://leetcode.com/problems/rotate-list/)   
#### 1. 刚开始思路
#### 2. 刚开始代码  
#### 3. 犯的错或者没想到的点  
#### 4. 新的思路  
#### 5. 新的代码  
#### 6. 总结及关联题目 


### [61. Rotate List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)  
Follow up: Could you do this in one pass?  
#### 1. 刚开始思路
#### 2. 刚开始代码  
#### 3. 犯的错或者没想到的点  
#### 4. 新的思路  
#### 5. 新的代码  
#### 6. 总结及关联题目 
