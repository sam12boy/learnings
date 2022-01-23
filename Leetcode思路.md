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
其实因为之前看过嘛，就是保证快慢指针之前的差为n
#### 2. 刚开始代码  
```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy=new ListNode(0);
        ListNode slow=dummy;slow.next=head;
        ListNode fast=head;
        for (int i=0;i<n;i++){
            fast=fast.next;
           
        }
        while (fast!=null){
            slow=slow.next;
            fast=fast.next;
        }
        slow.next=slow.next.next;
        return dummy.next;
    }
}
```
#### 3. 犯的错或者没想到的点  
#### 4. 新的思路  
#### 5. 新的代码  
#### 6. 总结及关联题目  

### [24. Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/)   （未做）
（1->2->3->4） (2->1->4->3)
#### 1. 刚开始思路  
刚开始有两个想法一种是1直接去连4，但是太远了，边界值不好考虑  
于是我想就近一步步来 dummy->2 1->3 2->1 这一步是没啥问题  
但问题处在你移动好之后的新位置和指针所在位置  
见下图
![](https://camo.githubusercontent.com/d331014ce3427950fbb92631034b8f616c49cd482f4695e1276e1ecac7ac420c/68747470733a2f2f77696e646c69616e672e6f73732d636e2d6265696a696e672e616c6979756e63732e636f6d2f32345f362e6a7067)
#### 2. 刚开始代码  
#### 3. 犯的错或者没想到的点  
#### 4. 新的思路  
#### 5. 新的代码  
#### 6. 总结及关联题目 


### [125. Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)   
#### 1. 刚开始思路  
1.前后分别遍历，碰到非数字和字母就跳过
#### 2. 刚开始代码   
```java
class Solution {
    public boolean isPalindrome(String s) {
        s=s.toLowerCase();
        int i=0,j=s.length()-1;
        while(i<j){
            while (!isAlphanumeric(s.charAt(i))){
                i++;
            }
            while (!isAlphanumeric(s.charAt(j))){
                j--;
            }
            if (s.charAt(i)!=s.charAt(j)){
                return false;
            }
            i++;
            j--;
        }
        return true;
    }
    private boolean isAlphanumeric(char c){
        if (c>='0'&& c<='9' || c>='a'&&c<='z'){
            return true;
        }
        return false;
    }
}
```
#### 3. 犯的错或者没想到的点   
没考虑到i,j不断走越界的情况，在",."这种反例下，s.charAt(i)!=s.charAt(j)这一句就会越界
#### 4. 新的思路   
仔细想了下，当把字符串整个都遍历完，仍然没有数字或者字母的情况说明，这个字符串去除数字和字母就是空字符，按照题意应该返回true
#### 5. 新的代码   
```java
class Solution {
    public boolean isPalindrome(String s) {
        s=s.toLowerCase();
        int i=0,j=s.length()-1;
        while(i<j){
            while (!isAlphanumeric(s.charAt(i))){
                i++;
                if (i==s.length()){
                    return true;
                }
            }
            while (!isAlphanumeric(s.charAt(j))){
                j--;
            }
            if (s.charAt(i)!=s.charAt(j)){
                return false;
            }
            i++;
            j--;
        }
        return true;
    }
    private boolean isAlphanumeric(char c){
        if (c>='0'&& c<='9' || c>='a'&&c<='z'){
            return true;
        }
        return false;
    }
}
```
#### 6. 总结及关联题目 
