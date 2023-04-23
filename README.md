## 27. Remove Element
链表去重，快慢指针
+ 两种情况下都需要fast++，但是只有遇到不需要去重的元素时才更新slow和数组
## 26. Remove Duplicates from Sorted Array
链表去重，快慢指针
+ 两种情况下都需要fast++，但是只有元素不同时才需要更新slow和数组
## 25. Reverse Nodes in k-Group
链表结合递归，每次翻转k个节点
+ 不用翻转的情况：剩下的少于k个
+ 左闭右开翻转hair和tail之间的节点，之后要让hair.next指向tail
+ 递归翻转从tail开始的节点
## 24. Swap Nodes in Pairs
链表，注意hair，first，second之间的逻辑
+ ListNode hair = new ListNode(-1, head);
+ 更好的方法是递归
## 23. Merge k Sorted Lists
强制使用PriorityQueue，初始阶段将所有链表加入，每次剥一个节点之后加回去
+ PriorityQueue<ListNode> queue = new PriorityQueue<>((a,b)->(a.val-b.val))
+ 初始offer(node)，之后每次poll()，剥完之后offer(node.next)
+ 注意null链表，注意剥完节点判断null
+ 熟练使用hair接在head前面
## 22. Generate Parentheses
回溯，初始空past与空res，每次要么加左括号要么加右括号
+ 最终状态为left==0，right==0。继续permute的前提是left>=0，right>=0，left<=right
## 21. Merge Two Sorted Lists
首先设置和记录hair的位置，然后依次比较两个列表head的val大小
+ hair保证空链表不出错
+ 一个链表空了之后将另一个链表的head连上，不需要继续遍历
## 20. Valid Parentheses
开始使用Stack，左括号压入栈，遇到右括号需要保证栈非空然后弹出栈检查匹配，遍历完字符串需要保证栈空
+ Stack：push() | pop() | peek() | isEmpty()
## 19. Remove Nth Node From End of List
双指针，fast先跑n步，然后fast和slow一起跑，最后删除slow.next
+ 两个都从hair开始，防止删除head的特殊情况
+ 判断slow：如果在hair，说明应当删除head返回head.next，否则返回hair.next
## 18. 4Sum
超过三个数字的和就可以写成通解形式了，针对n>2的情况选取start作为下一个元素，然后从start+1开始考虑n-1的情况
+ 保存结果：List<List<Integer>>
+ low和high找到结果后要同时滑动两个指针，如果不符合结果要滑动其中一侧指针
+ 转换为List：Arrays.asList(a,b,c)
+ 转换为Array：ArrayList.toArray(data)
## 17. Letter Combinations of a Phone Number
先写好每个按钮对应的字母，然后permute
+ 全局变量写在类里面所有函数外面
+ 要求返回List时：List<> ret = new ArrayList<>();
## 16. 3Sum Closest
排序之后，先确定first的位置，然后low和high双指针
+ 注意更新结果的逻辑
+ 移动low和high要使sum往有利的方向移动
## 15. 3Sum
首先排序，然后确定最小的元素，剩下的利用low和high指针找twoSum
+ 排序：Arrays.sort(nums);
+ 初始化二维数组：List<List<Integer>> res = new ArrayList<>();
+ 过滤重复元素：nums[low]==left | nums[high]==right
## 14. Longest Common Prefix
指针从0开始检验每个字符串对应位置是否与第一个字符串相同
+ 需要注意第一个字符串与每个字符串的长度
## 13. Roman to Integer
扫描字符串，依次匹配百位十位个位的数字
+ 较快的方法是直接记录可能的字母组合与对应数值
+ 需要注意每一位匹配的顺序
+ 初始化Array：int[5] = {1,2,3,4,5};
+ 子串：s.substring(start,end)
## 12. Integer to Roman
根据数字大小范围，依次向字符串增加罗马字母
+ 最快的方法是每一位都直接编写好对应字典
## 11. Container With Most Water
左右双指针，从两侧向中间移动
+ 确保每次移动短边，这样有可能获得更大的体积
## 10. Regular Expression Matching
完善了很久的hard题，属于动态规划+考虑基础情况
+ 计算之前先查备忘录，计算之后写进备忘录
+ 基础情况：x=0，y=0
+ 只有x>0：无法匹配，只有y>0：检查y是否全为.*
+ x与y匹配或y为.：检查memo(x-1)(y-1)
+ x与y不匹配：考虑y是*，y+1是*的情况
## 9. Palindrome Number
只是普通的判断数字是否为回文，负数全为假，剩余只要转换成数组即可
+ 注意0的特殊情况
+ 可以直接生成翻转整数判断相等
## 8. String to Integer (atoi)
需要处理：空格，符号，数字溢出
+ 注意index++的循环外面一定要有index<s.length()
+ 判断字符串：Character.isDigit()
+ String转换Integer：Integer.parseInt()
## 7. Reverse Integer
反转数值用取模/乘10加余/整除10循环
+ 检查是否溢出时尽量不要使用加法和乘法，减法和除法一般是安全的
## 6. Zigzag Conversion
建立一个Array的StringBuilder，轮流添加字符，注意指针改变方向
+ 需要注意numRows为一行时的特殊情况：不需要记录和改变方向
+ StringBuilder常用：.append()/.toString()
## 5. Longest Palindromic Substring
Brute Force复杂度为O(n^2)，同时检查奇数长度（从同一个字符开始）和偶数长度（从两个相邻字符开始）
+ DP需要大小为n^2的memo
+ 初始将对角线置为1
+ 新的位置：如果两个元素相同，判断是否为相邻位置（不需要额外信息），不相邻则需要查询表前一个位置的信息
## 4. Median of Two Sorted Arrays
要求是O(log(m+n))，分治法没有思路，直接merge只能得到O(m+n)
## 3. Longest Substring Without Repeating Characters
滑动窗口记录可行字串左右位置
+ 滑动窗口：right加入窗口->right++->根据需要left++->更新结果
+ Array：array.length | String：s.length()
## 2. Add Two Numbers
准备hair记录返回结果的链表，每一位为两个数对应位置加进位
+ 可以将p1!=null/p2!=null/carry!=0放进同一个循环做加法
## 1. Two Sum
遍历列表用HashMap记录需要的后一个元素的值/前一个元素的位置键值对
+ 创建HashMap：HashMap<T,T> variable=new HashMap<T,T>();
+ 数组长度：nums.length
+ HashMap包含：containsKey()
# Leetcode-notes
Starting fresh in Java. Noting down thoughts and comments.