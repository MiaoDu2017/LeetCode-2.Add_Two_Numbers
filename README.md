# LeetCode-2.Add_Two_Numbers

Problem:

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Example:

Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.

Solution Python 3:

Definition for singly-linked list.
class ListNode:
  def __init__(self, x):
    self.val = x
    self.next = None

class Solution:

    def addTwoNumbers(self, l1, l2 ,c = 0):
        
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        
        val = l1.val + l2.val + c
        c = val // 10 # to the nearest whole number
        ret = ListNode(val % 10 )  # if more than 10, ret could be 0, carry = 1
        
        if (l1.next != None or l2.next != None or c != 0):
            if l1.next == None:
                l1.next = ListNode(0)
            if l2.next == None:
                l2.next = ListNode(0)
            ret.next = self.addTwoNumbers(l1.next,l2.next,c)
        return ret
