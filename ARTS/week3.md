第2周

Algorithm

2. Add Two Numbers
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.
You may assume the two numbers do not contain any leading zero, except the number 0 itself.
Example:
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.


/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        int carryFlag = 0;
        ListNode add1 = l1;
        ListNode add2 = l2;
        ListNode resultNode = new ListNode(0);
        ListNode resultTmp = resultNode;
        while ( add1 != null || add2 != null || carryFlag != 0 ){
            resultTmp.next = new ListNode(0);
            resultTmp = resultTmp.next;
            if(add1 == null) add1 = new ListNode(0);
            if(add2 == null) add2 = new ListNode(0);
            int sumTmp = add1.val + add2.val + carryFlag;
            carryFlag = sumTmp / 10;
            resultTmp.val = sumTmp % 10;
            add1 = add1.next;
            add2 = add2.next;           
        }
        resultNode = resultNode.next;
        return resultNode;        
    }
}

leetcode的题这周第二次刷，runtime distributio从上周的50%+提到了98%，有进步值得开心。可没有抽出更多时间，仔细研究每道题的算法，尤其把最优解法掌握。
之后的每周这一任务应该抽平常时间提前做，不能再留到周日匆匆忙忙的完成任务。

Review

java中的不可变对象
https://dzone.com/articles/java-immutable-objects

Technique

关于SSH无密码登录

linux系统中，用户家目录下的.ssh隐藏文件夹，用于保存此用户ssh登录的信息，包括配置的ssh无密码登录信息。
将文件夹删除后，此用户配置的ssh无密码登录失效。
再次使用ssh命令，会重新生成.ssh文件夹。

Share

正式转岗后端开发工程师快三个月了，一大半的时间在跟linux打交道，学调度、写shell脚本。
java千万不能落下，看到一篇《Java 后端自学之路》总结的不错，里面有些内容学习了一些，之后要抽时间重点掌握的是web框架进阶部分。
自己目前的工作中能接触的web框架属于web框架基础，业余抽时间学习web框架进阶非常有必要。
http://objcoding.com/2018/02/07/javaweb-learning/
