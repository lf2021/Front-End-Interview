# leetcode

前300道题目（不包括困难级别题目）思路，仅供参考

- [leetcode](#leetcode)
  - [面试题 02.01. 移除重复节点](#面试题-0201-移除重复节点)
  - [面试题 16.11. 跳水板](#面试题-1611-跳水板)
  - [剑指 Offer 22. 链表中倒数第k个节点](#剑指-offer-22-链表中倒数第k个节点)
  - [1. 两数之和](#1-两数之和)
  - [3. 无重复字符的最长子串](#3-无重复字符的最长子串)
  - [6. Z字形变换](#6-z字形变换)
  - [7. 整数反转](#7-整数反转)
  - [9. 回文数](#9-回文数)
  - [11. 盛最多水的容器](#11-盛最多水的容器)
  - [12. 整数转罗马数字](#12-整数转罗马数字)
  - [13. 罗马数字转整数](#13-罗马数字转整数)
  - [14. 最长公共前缀](#14-最长公共前缀)
  - [15. 三数之和](#15-三数之和)
  - [16. 最接近的三数之和](#16-最接近的三数之和)
  - [17. 电话号码的字母组合](#17-电话号码的字母组合)
  - [19. 删除链表的倒数第N个节点](#19-删除链表的倒数第n个节点)
  - [20. 有效的括号](#20-有效的括号)
  - [21. 合并两个有序链表](#21-合并两个有序链表)
  - [24. 两两交换链表中的节点](#24-两两交换链表中的节点)
  - [26. 删除排序数组中的重复项](#26-删除排序数组中的重复项)
  - [27. 移除元素](#27-移除元素)
  - [28. 实现 strStr()](#28-实现-strstr)
  - [31. 下一个排列](#31-下一个排列)
  - [33. 搜索旋转排序数组](#33-搜索旋转排序数组)
  - [35. 搜索插入位置](#35-搜索插入位置)
  - [53. 最大子序和](#53-最大子序和)
  - [58. 最后一个单词的长度](#58-最后一个单词的长度)
  - [61. 旋转链表](#61-旋转链表)
  - [82. 删除排序链表中的重复元素 II](#82-删除排序链表中的重复元素-ii)
  - [83. 删除排序链表中的重复元素](#83-删除排序链表中的重复元素)
  - [112. 路径总和](#112-路径总和)
  - [125. 验证回文串](#125-验证回文串)
  - [141. 环形链表](#141-环形链表)
  - [160. 相交链表](#160-相交链表)
  - [203. 移除链表元素](#203-移除链表元素)
  - [206. 反转链表](#206-反转链表)
  - [209. 长度最小的子数组](#209-长度最小的子数组)
  - [215. 数组中的第K个最大元素](#215-数组中的第k个最大元素)
  - [234. 回文链表](#234-回文链表)
  - [876. 链表的中间结点](#876-链表的中间结点)

## 面试题 02.01. 移除重复节点

```txt
双指针法，循环右指针即可
```

```js
var removeDuplicateNodes = function(head) {
    if(!head) return null;
    let left = head, right = left.next;
    let arr = [left.val];
    while(right) {
        if(arr.indexOf(right.val) !== -1) {
            left.next = right.next;
        }else {
            arr.push(right.val);
            left.next = right;
            left = left.next;
        }
        right = right.next;
    }
    return head;
};
```

## 面试题 16.11. 跳水板

```txt
动态规划
最开始全是短木板（k*shorter），然后每次都把上一次的一个短木板变为长木板。
```

```js
var divingBoard = function(shorter, longer, k) {
    if(k<=0)return [];
    let ans = [k*shorter];
    let diff = longer - shorter;
    if(diff === 0) return ans;
    for(let i=1;i<=k;i++){
        ans.push(ans[ans.length - 1]+diff);
    }
    return ans;
};
```

## 剑指 Offer 22. 链表中倒数第k个节点

```txt
双指针法：右指针先走k-1步，然后左右指针一起走。
```

```js
var getKthFromEnd = function(head, k) {
    let left = head;
    let right = head;
    for(let i=1;i<k;i++){
        right = right.next;
    }
    while(right.next) {
        right = right.next;
        left = left.next;
    }
    return left;
};
```

## 1. 两数之和

```txt
map用来存储遍历时候的元素-索引对
遍历一次列表，计算每个元素与target的差，判断一下map中存不存在这个键
时间复杂度：O(N)

举例：
  nums = [2, 7, 11, 15]， target = 9

  遍历第一轮：i = 0
    num = 9 - 2 = 7,
    7在map中不存在,将当前遍历元素添加进map，map = { 2: 0 }

  遍历第二轮： i = 1
    num = 9 - 7 = 2,
    2在map中是键，直接返回2对应值和当前的索引组成的数组 [0, 1]
```

```js
var twoSum = function(nums, target) {
    let map = new Map();
    for (let i = 0; i < nums.length; i++) {
        let num = target - nums[i];
        if (map.has(num)) {
            return [map.get(num), i];
        } else {
            map.set(nums[i], i);
        }
    }
};
```

## 3. 无重复字符的最长子串

```txt
遍历一轮，res保存遍历到的不重复的字符串，maxLen记录最大的长度

此方法只能求出最大的不重复子串的长度
时间复杂度：O(N)
```

```js
var lengthOfLongestSubstring = function(s) {
    let res = '';
    let maxLen = 0;
    let cur = 0;
    while (cur < s.length) {
        if (res.indexOf(s[cur]) === -1) {
            res += s[cur];
        } else {
            let index = res.indexOf(s[cur]);
            res = res.slice(index + 1) + s[cur]
        }
        maxLen = Math.max(maxLen, res.length);
        cur++;
    }
    return maxLen;
};
```

## 6. Z字形变换

```txt
这个Z字形变换的话相当于是有numRows行数据，要将字符串s中的每个字母依次从上往下再从下往上添加到这个numRows行中，
我只需要用一个列表去存放这numRows行数据，初始化列表中每个元素为空字符串，用一个pos指针来对应列表中第几个元素，
然后用一个flag来标识我是 从左往右 还是 从右往左 向数组中元素添加字母，最终只需将这个数组拼接起来

举例：s="leetcode" numRows=3

arr = ['', '', '']

1. ['l','','']
2. ['l','e','']
3. ['l','e','e']
4. ['l','et','e']
5. ['lc','et','e']
6. ['lc','eto','e']
7. ['lc','eto','ed']
8. ['lc','etoe','ed']

answer = "lcetoeed"
```

代码：

```js
var convert = function(s, numRows) {
  if(numRows===1)return s;
  const arr = [];
  for(let i=0;i<numRows;i++){
    arr[i]=''
  }
  let pos = 0;
  let down = false;
  for(let item of s){
    arr[pos]+=item;
    if(pos===0||pos===numRows-1){
      down=!down
    }
    pos+=down?1:-1;
  }
  return arr.join('')
};
```

## 7. 整数反转

```txt
原数x, 新数res。利用`int tmp = x % 10;` 。取个位，然后将其作为新数的最高位`res = res*10 + tmp;`，更新x：` x /= 10;`。重复上述操作，直到x = 0。此间不断判断是否溢出
```

## 9. 回文数

```txt
进阶不将整数转换为字符串，思路：
1.x是负数肯定不是回文数
2.x是0-9的数肯定是回文数
3.x>9的时候，又分两种可能：
  （1）奇数个数，类似x=121，
  （2）偶数个数，类似x=1221
  这两种情况初始化一个reverse变量为0，每次循环reverse都等于自身*10加上x的个位数（reverse=reverse*10+x%10），x整除10（x/=10）,直到x的值比reverse小停止循环。
  只需判断一下reverse与x是否相等（偶数个数），reverse对10整除后是否与x相等（奇数个数）

例如 x=121（奇数个数）
  1、reverse=1, x=12
  2、reverse=12, x=1
  reverse/10 = x （是回文数）

例如 x=1221（偶数个数）
  1、reverse=1, x=122
  2、reverse=12, x=12
  reverse = x （是回文数）
```

代码：

```js
var isPalindrome = function(x) {
    if(x<0||x!==0&&x%10==0)return false;
    else if(x<=9)return true
    else{
        var reverse = 0;
        while(x>reverse){
            reverse=reverse*10+x%10;
            x=parseInt(x/10)
        }
        return reverse===x||parseInt(reverse/10)===x
    }  
};
```

## 11. 盛最多水的容器

```txt
用双指针法，left和right指针分别指向数组的头和尾，这个时候可以计算一下left和right对应区间可容纳的水:
res = (right-left) * Math.max(height[left],height[right])
当左右指针移动时，res变大只有一种情况，那就是left和right指针对应的数中小的那个数移动了之后变大了。
也就时长方形的宽度在减小，要想使面积变大，必须使得高度变大。
```

代码：

```js
var maxArea = function(height) {
  var left=0, right=height.length-1;
  var max = 0;
  while(left<right){
    max = Math.max(max, [right-left]*Math.min(height[left], height[right]));
    if(height[left]<height[right]){
      left++
    }else{
      right--
    }
  }
  return max
};
```

## 12. 整数转罗马数字

```txt
简单粗暴，罗列出个十百千位的所有可能性：
个位：['','I','II','III','IV','V','VI','VII','VIII','IX']
十位：['','X','XX','XXX','XL','L','LX','LXX','LXXX','XC']
百位：['','C','CC','CCC','CD','D','DC','DCC','DCCC','CM']
千位：['','M','MM','MMM']

然后根据给的num，拿到个十百千位的罗马数字拼接起来
```

## 13. 罗马数字转整数

将所有可能的情况保存在一个对象中：

```js
map = {
  'I' : 1,
  'IV': 4,
  'V' : 5,
  'IX': 9,
  'X' : 10,
  'XL': 40,
  'L' : 50,
  'XC': 90,
  'C' : 100,
  'CD': 400,
  'D' : 500,
  'CM': 900,
  'M' : 1000,
};
```

然后对给定的罗马字符进行遍历，每次需要判断一下：
连续两个字符在对象是否存在，存在就用这连续两个字符的值；不存在就用当前遍历的字符的值

## 14. 最长公共前缀

```js
/**
 * @param {string[]} strs
 * @return {string}
 */
var longestCommonPrefix = function(strs) {
    if(!strs.length)return ''
    var ans = strs[0];
    for(let i=1; i<strs.length; i++){
        let j=0;
        for(;j<ans.length && j<strs[i].length;j++){
            if(ans[j] !== strs[i][j]){
                break
            }
        }
        ans = ans.slice(0, j);
    }
    return ans
};
```

```txt
先拿出第一个字符串first，再遍历剩余的字符串，每一次遍历：
对每一个字符串str判断的与first公共前缀的字符串，遍完将将first重新赋值为公共前缀，再
再遍历下一个字符串，最后得到的first就是所有字符串的公共前缀

举例： strs = ["flower","flow","flight"]

first = "flower"
遍历剩余的字符串：
    遍历第一次：
        str = "flow", 判断此时与first相同的前缀  first = "flow"
    遍历第二次：
        str = "flight"，判断此时与first相同的前缀  first = "fl"
遍历结束，公共前缀就是first
```

## 15. 三数之和

```js
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var threeSum = function(nums) {
    var ans = [];
    nums.sort((a,b) => a-b);
    for(let i=0; i<nums.length-2; i++){
        if(nums[i]>0)break;
        if(nums[i]===nums[i-1])continue // 去重
        var L=i+1,R=nums.length-1;
        while(L<R){
            var sum=nums[i]+nums[L]+nums[R];
            if(sum===0){
                ans.push([nums[i],nums[L],nums[R]]);
                while(L<R&&nums[L]===nums[L+1]){L++} // 去重
                while(L<R&&nums[R]===nums[R-1]){R--} // 去重
                L++;
                R--;
            }else if(sum>0){
                R--;
            }else{
                L++;
            }
        }
    }
    return ans;
};
```

```txt
首先对数组进行排序，排序后固定一个数 nums[i]nums[i]，再使用左右指针指向 nums[i]nums[i]后面的两端，数字分别为 nums[L]nums[L] 和 nums[R]nums[R]，计算三个数的和 sumsum 判断是否满足为 00，满足则添加进结果集
如果 nums[i]nums[i]大于 00，则三数之和必然无法等于 00，结束循环
如果 nums[i]nums[i] == nums[i-1]nums[i−1]，则说明该数字重复，会导致结果重复，所以应该跳过
当 sumsum == 00 时，nums[L]nums[L] == nums[L+1]nums[L+1] 则会导致结果重复，应该跳过，L++L++
当 sumsum == 00 时，nums[R]nums[R] == nums[R-1]nums[R−1] 则会导致结果重复，应该跳过，R--R−−
时间复杂度：O(n^2)
```

## 16. 最接近的三数之和

```txt
思路一：复杂度O(N^3)
三层循环，将三个数相加，和与target求差的绝对值最小的时候，返回这三个数的和

思路二：复杂度 O(N^2)
先对nums进行排序，然后对nums做一层遍历，当前遍历元素nums[i]，用两个指针L，R分别为 i+1 和 nums.length-1，求和 sum=nums[i]+nums[L]+nums[R]，初始化ans（到target距离最小的和）为前三位加起来的和，判断：
1. 若sum 到 target 的距离比 ans 到 target 的距离小，则更新ans为sum
2. 若sum < target, L++
3. 若sum > target, R--
4. 若sum = target, 返回sum
```

```js
// 思路一：
var threeSumClosest = function(nums, target) {
  var min = Infinity;
  var ans;
  for(let i=0;i<nums.length;i++){
    for(let j=i+1;j<nums.length;j++){
      for(let k=j+1;k<nums.length;k++){
        var sum = nums[i]+nums[j]+nums[k];
        if(min > Math.abs(sum-target)){
          min = Math.abs(sum - target)
          ans = sum;
        }
      }
    }
  }
  return ans
};
// 思路二：
var threeSumClosest = function(nums, target) {
  var res=nums[0]+nums[1]+nums[2], min=Infinity;
  nums.sort((a,b)=>a-b);
  for(let i=0;i<nums.length-2;i++){
    var L=i+1, R=nums.length-1;
    while(L<R){
      var sum = nums[i]+nums[L]+nums[R];
      if(Math.abs(sum-target) < Math.abs(res-target)){
        res = sum;
      } else if(sum < target){
        L++
      } else if(sum > target){
        R--
      } else if(sum === target){
        return sum
      }
    }
  }
  return res;
};
```

## 17. 电话号码的字母组合

```txt
首先用一个对象保存所有可能的情况
遍历digits，拿到对应的字母
res为空数组的时候初始化第一个按键产生的字母
到了第二个以后的按键只用现有res中取到所有现有字母组合并和此按键的元素拼接字符串即可

举例：digits='23'
初始化res = []
遍历digits第一次：
  res = ['a', 'b', 'c']
遍历digits第二次：得到字母 'def'
  对 'def' 从第二个（索引为1）进行遍历，tmp = ['ae', 'af', 'be', 'bf', 'ce', 'cf']
  将res的每一项添加 'def' 的第一项，即 res = ['ad', 'bd', 'cd']
  然后将 tmp 的每一项添加到 res 中，得到最终的结果 ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"]
```

```js
var letterCombinations = function(digits) {
  const map = {
      2: "abc",
      3: "def",
      4: "ghi",
      5: "jkl",
      6: "mno",
      7: "pqrs",
      8: "tuv",
      9: "wxyz"
  };
  const res = [];
  for(let num of digits){
    let w = map[num];
    if(res.length!==0){
      let tmp = [];
      for(let i=0;i<res.length;i++){
        for(let j=1;j<w.length;j++){
          tmp.push(res[i]+w[j]);
        }
        res[i]+=w[0];
      }
      res.push(...tmp);
    }else{
      res.push(...w)
    }
  }
  return res;
};
```

## 19. 删除链表的倒数第N个节点

```txt
首先先设置一个辅助头结点，让辅助头结点指向给定的head链表，然后用快慢指针low和fast，初始都指向辅助头结点
先让fast指针走n步，然后fast和low指针同时走，当fast指针走到最后的时候，这个时候的low指针的下一个结点就是我们要删除的。
```

```js
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} n
 * @return {ListNode}
 */
var removeNthFromEnd = function(head, n) {
  var pHead = new ListNode(-1); // 辅助头结点
  pHead.next = head;
  var cur = pHead;
  var pre = pHead;
  for(let i=0;i<n;i++){
    cur=cur.next;
  }
  while(cur && cur.next){
    pre = pre.next;
    cur = cur.next;
  }
  pre.next = pre.next.next;
  return pHead.next;
};
```

## 20. 有效的括号

```txt
字符串的长度为奇数肯定是false
对字符串遍历，碰到左括号 '[({' 就压入栈中，碰到右括号 '])}' ，将栈顶元素弹出，与当前遍历字符判断一下是不是一对括号，不是返回false
遍历结束后判断一下栈中是否还有元素，有则是false，没有则是true
```

```js
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
  if(s.length % 2 === 1) return false
  var stack = [];
  var map = {
    ")": "(",
    "}": "{",
    "]": "["
  };
  for(let i=0; i<s.length; i++) {
    var str = s[i];
    if(str==='('||str==='{'||str==="["){
      stack.push(str);
    } else {
      if (stack.pop() !== map[str]) {
        return false
      }
    }
  }
  if (stack.length !== 0) return false
  return true
};
```

## 21. 合并两个有序链表

```txt
创建一个辅助头节点head，用指针p指向head，
用两个指针p1 p2 分别指向l1 l2 ，当p1和p2都存在的时候，判断一下p1.val和p2.val的大小：
 p1.val < p2.val. => p.next = p1
 否则 p.next = p2
p1 p2只要有一个为空，就结束循环，看一下p1 p2谁还存在:
 p1存在：p.next = p1
 p2存在：p.next = p2
最后返回head.next，也就是辅助头节点的下一个节点
```

```js
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var mergeTwoLists = function(l1, l2) {
    var p1 = l1, p2 = l2;
    var head = new ListNode(-1); // 辅助头节点
    var p = head;
    while(p1 && p2) {
        var n1 = p1.val;
        var n2 = p2.val;
        if(n1 < n2) {
            p.next = p1;
            p1 = p1.next;
        }else {
            p.next = p2;
            p2 = p2.next;
        }
        p = p.next
    }
    if(p1) {p.next = p1}
    if(p2) {p.next = p2}
    return head.next
};
```

## 24. 两两交换链表中的节点

```txt
构建一个哨兵节点0，例如：1->2->3->4
则：0->1->2->3->4
让p指向0，pre指向1，cur指向2
对其做指针指向操作：p指向cur，（pre.next是cur的next），cur指向pre
对链表做一次遍历即可。
时间复杂度O(N),空间复杂度O(1)
```

```js
var swapPairs = function(head) {
    let node = new ListNode(-1);
    node.next = head;
    let p = node;
    while(p && p.next && p.next.next) {
        let pre = p.next;
        let cur = pre.next;
        p.next = cur;
        pre.next = cur.next;
        cur.next = pre;
        p = pre;
    }
    return node.next;
};
```

## 26. 删除排序数组中的重复项

```txt
倒序遍历数组，判断一下当前元素与下一个元素是否相同，如果相同就删除当前元素，遍历结束返回数组的长度
```

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var removeDuplicates = function(nums) {
  for(let i=nums.length; i>0; i--) {
    if(nums[i] === nums[i-1]){
      nums.splice(i, 1)
    }
  }
  return nums.length;
};
```

## 27. 移除元素

```txt
思路1：
倒序遍历数组，判断一下当前元素与下一个元素是否相同，如果相同就删除当前元素，遍历结束返回数组的长度

思路2：
遍历数组nums，遍历指针为i，总长度为ans
在遍历过程中如果出现数字与需要移除的值不相同时，则i自增1，继续下一次遍历
如果相同的时候，则将nums[i]用nums[ans-1]覆盖，即当前数字和数组最后一个数字进行交换，交换后就少了一个元素，故而ans自减1
```

```js
// 思路1
var removeElement = function(nums, val) {
  for(let i=nums.length-1;i>=0;i--) {
    if(nums[i] === val) {
      nums.splice(i, 1);
    }
  }
  return nums.length;
};

// 思路2
var removeElement = function(nums, val) {
  var ans = nums.length;
  for(let i=0;i<ans;){
    if(val === nums[i]){
      nums[i] = nums[ans-1]
      ans--;
    }else{
      i++;
    }
  }
  return ans
};
```

## 28. 实现 strStr()

```txt
直接调用indexOf()方法就好了
```

```js
var strStr = function(haystack, needle) {
  if(!needle) return 0;
  return haystack.indexOf(needle)
};
```

## 31. 下一个排列

```txt
1.从数组的末尾寻找第一对升序排列的值i,j
2.在j后面的数组现在肯定都是降序排列的，包括j自己
3.此时，在[j, nums.length - 1]的区间从后往前寻找第一个
  大于nums[i]的位置k，注意这里一定是大于，等于不可以
4.交换nums[i] 和 nums[k] 处的值
5.此时，区间[j, nums.length]区间内肯定是降序排列的
  所以此时需要将此区间内的数组改成降序排列才能得到更小的值
6.因为[j, nums.length]区间内的数组是降序，所以
  收尾交换数据即可完成升序排列
```

```js
var nextPermutation = function(nums) {
  if (nums.length < 2) return nums;
  let len = nums.length;
  let i = len - 2;
  let j = len - 1;
  let k = len - 1;
  // 寻找从数组末尾开始的第一个升序的i,j
  while (i >= 0 && nums[i] >= nums[j]) {
    i--;
    j--;
  }
  // 说明数组是降序排列的
  if (i < 0) return nums.sort((a, b) => a - b);
  // 从数组末尾寻找第一个比nums[i]大的值
  // 注意边界和相等问题
  while (k > i && nums[i] >= nums[k]) {
    k--;
  }
  // 交换i，k处的值
  swap(nums, i, k);
  // j后的数据现在肯定是降序排列,转化为升序排列
  // 收尾依次交换位置即可
  while (len > j) {
    swap(nums, j, len - 1);
    len--;
    j++;
  }

  function swap (nums, i, k) {
    let temp = nums[i];
    nums[i] = nums[k];
    nums[k] = temp;
  }

  return nums;
}
```

## 33. 搜索旋转排序数组

```txt
二分法：
L指向数组第一个数，R指向数组最后一个数，mid为L和R的中间数，当L<=R的时候，判断：
  1）若中位数刚好等于target，则返回这个mid
  2）若中位数比第一个数大，说明[L, mid]这个区间的数是有序的，继续判断：
    若target在[L, mid]之间，则另R=mid-1
    否则另L=mid+1
  3）若中位数比最后一个数小，说明[mid, R]这个区间的数是有序的，继续判断：
    若target在[mid, R]之间，则另L=mid+1
    否则另R=mid-1
循环结束都不满足条件就返回-1
```

```js
var search = function(nums, target) {
    let L = 0, R = nums.length - 1;
    while (L <= R) {
        let mid = (L + R) >> 1;
        if (target === nums[mid]) {
            return mid;
        }
        if (nums[mid] >= nums[L]) { // mid左边是有序的数组
            if(target >= nums[L] && target <= nums[mid]) { // target在 [L, mid]之间，且有序
                R = mid - 1;
            } else { // target不在 [L, mid]之间
                L = mid + 1;
            }
        }else { // mid右边是有序的数组
            if(target >= nums[mid] && target <= nums[R]) { // target在[mid, R]之间，且有序
                L = mid + 1;
            } else { // target不在 (mid, R]之间
                R = mid - 1;
            }
        }
    }
    return -1
};
```

## 35. 搜索插入位置

```txt
思路1：
暴力遍历

思路2:
二分法：
用两个指针left right分别记录左右下标，每次取得左右下标的中位数的下标mid，判断一下中位数与target的大小：
  若比target小，说明target在mid右边，让left=mid+1;
  否则的话在mid左边（可能就是mid这个数），让right=mid;
```

```js
// 思路1：
var searchInsert = function(nums, target) {
    for(let i=0; i<nums.length;i++) {
        if(nums[i] >= target) {
            return i;
        }
    }
    return nums.length;
};

// 思路2:
var searchInsert = function(nums, target) {
    var left=0, right=nums.length-1;
    if(target > nums[right]) {
        return right+1;
    }
    while(left < right) {
        var mid = (left + right) >>> 1;
        if(target > nums[mid]) {
            left = mid + 1;
        }else {
            right = mid;
        }
    }
    return left;
};
```

## 53. 最大子序和

```txt
遍历一次，从第一个大于0的数开始，求和并且每一步更新和的最大值，求和过程中如果小于0，则抛弃这个，从后续大于0的数继续。
```

```js
var maxSubArray = function(nums) {
    var maxSum = nums[0];
    var num = nums[0];
    for(let i=1; i<nums.length; i++) {
        if (num < 0) {
            num = nums[i];
        }else {
            num += nums[i];
        }
        maxSum = Math.max(maxSum, num);
    }
    return maxSum;
};
```

## 58. 最后一个单词的长度

```txt
太简单了，去除一下首尾的空格，然后分割一下去最后一个的长度
```

```js
var lengthOfLastWord = function(s) {
    let arr = s.trim().split(" ");
    return arr[arr.length-1].length;
};
```

## 61. 旋转链表

```txt
思路1:
双指针法：右指针先走k步，然后左右指针一起走，在右指针走到最后的时候左指针的位置就是要动的地方。

思路2:
求出链表的size，然后可以求出链表中要动的地方。
```

```js
// 思路1
var rotateRight = function(head, k) {
    if(!head) return null;
    let left = head;
    let right = head;
    for(let i = 0; i < k; i++) {
        right = right.next;
        if(!right){
            right = head;
        }
    }
    while(right.next) {
        left=left.next;
        right=right.next;
    }
    if(!left.next) return head;
    let node = left.next;
    left.next=null;
    let p = node;
    while(p.next) {
        p = p.next;
    }
    p.next = head;
    return node;
};

// 思路2
var rotateRight = function(head, k) {
    if(!head || !head.next) return head;
    let left = head;
    let right = head;
    let size = 1;
    while(right.next) {
        size++;
        right = right.next;
    }
    k = size - k % size;
    while(k > 1) {
        left = left.next;
        k--;
    }
    if(!left.next) return head;
    let node = left.next;
    left.next = null;
    let p = node;
    while(p.next) {
        p = p.next;
    }
    p.next = head;
    return node;
};
```

## 82. 删除排序链表中的重复元素 II

```txt
快慢指针
  快指针：跳过重复数，记录下一个前面没有重复数的节点位置
  慢指针：标记重复数字出现起点，根据链表特性，负责与下一个快指针相连
```

```js
var deleteDuplicates = function(head) {
    let node = new ListNode(-1); // 哨兵节点
    node.next = head;
    let fast = node.next;
    let slow = node;
    while(fast) {
        if(fast.next && fast.next.val === fast.val) {
            let sameVal = fast.val; // 先把相等的值保存下来
            while(fast && fast.val === sameVal) {
                fast = fast.next;
            }
            slow.next = fast;
        }else{
            slow.next = fast;
            slow = fast;
            fast = fast.next;
        }
    }
    return node.next;
};
```

## 83. 删除排序链表中的重复元素

```txt
直接法，简单
```

```js
var deleteDuplicates = function(head) {
    let p = head;
    while(p && p.next) {
        if(p.val === p.next.val){
            p.next = p.next.next;
        }else{
            p = p.next;
        }
    }
    return head;
};
```

## 112. 路径总和

```txt
递归
  1. 转为判断，左、右子树能否找出满足和为 sum - 父节点值 的路径
  2. 当遍历到叶子节点时，因为已经没有子节点了，如果 sum 等于当前节点的值，就返回 true
```

```js
var hasPathSum = function(root, sum) {
  // 根节点为空
  if (root === null) return false;
  
  // 叶节点 同时 sum 参数等于叶节点值
  if (root.left === null && root.right === null) return root.val === sum;

  // 总和减去当前值，并递归
  sum = sum - root.val
  return hasPathSum(root.left, sum) || hasPathSum(root.right, sum);
};
```

## 125. 验证回文串

```txt
思路1:
用正则将字符串中所有的非数字字母字符替换成空字符，然后将新的字符全部变成小写，字符翻转判断是否相等。

思路2:
用正则将字符串中所有的非数字字母字符替换成空字符，然后将新的字符全部变成小写，然后用双指针法判断是否是回文字符。
```

```js
// 思路1:
var isPalindrome = function(s) {
    s = s.replace(/\W/g, '').toLowerCase();
    return s === s.split('').reverse().join('');
};


// 思路2:
var isPalindrome = function(s) {
    let str = s.replace(/[^0-9a-zA-Z]/g, '').toLowerCase();
    var left = 0, right = str.length-1;
    while(left < right) {
        if(str[left] !== str[right]) {
            return false;
        }
        left++;
        right--;
    }
    return true;
};
```

## 141. 环形链表

```txt
思路1:
用一个列表去存储每次遍历的节点，只需要在每次遍历的时候判断一下当前节点是否已经存在即可

思路2:
快慢指针，只要链表存在环，那么快慢指针总会相遇。
```

```js
// 思路1
var hasCycle = function(head) {
    let p = head;
    let nodes = [];
    while(p) {
        if(nodes.indexOf(p) !== -1){
            return true;
        }
        nodes.push(p)
        p = p.next;
    }
    return false;
};

// 思路2
var hasCycle = function(head) {
    if(!head || !head.next) return false
    let slow = head;
    let fast = head.next;
    while(slow !== fast) {
        slow = slow.next;
        if(fast && fast.next) {
            fast = fast.next.next;
        }else{
            return false
        }
    }
    return true;
};
```

## 160. 相交链表

```txt
相交链表 headA headB，同时遍历这两个链表，当headA遍历完了遍历headB，当headB遍历完了遍历headA
也就是遍历一次headA+headB（拼起来）和headB+headA

headA: 4->1->8->4->5
headB: 5->0->1->8->4->5

headA+headB: 4->1->8->4->5->5->0->1->8->4->5
headB+headA: 5->0->1->8->4->5->4->1->8->4->5

可以看到在8的地方相遇了
```

```js
var getIntersectionNode = function(headA, headB) {
    let p1=headA;
    let p2=headB;
    while(true){
        if(p1 === p2) return p1;
        p1 = p1 ? p1.next : headB;
        p2 = p2 ? p2.next : headA;
    }
};
```

## 203. 移除链表元素

```txt
哨兵节点 + 双指针法
```

```js
var removeElements = function(head, val) {
    let node = new ListNode(-1);
    node.next = head;
    let pre = node;
    let cur = node.next
    while(cur) {
        if(cur.val === val) {
            pre.next = cur.next;
            cur = pre.next;
        }else{
            pre = cur;
            cur = cur.next;
        }
    }
    return node.next;
};
```

## 206. 反转链表

```txt
思路1: 用一个数组存储链表的val

思路2: 迭代
  一次遍历 时间复杂度O(N)，空间复杂度O(1)

思路3: 递归
```

```js
// 思路1:
var reverseList = function(head) {
    let arr = [];
    while(head) {
        arr.push(head.val);
        head=head.next;
    }
    arr.reverse();
    let node = new ListNode(-1);
    let p = node;
    arr.forEach(item => {
        p.next = new ListNode(item);
        p=p.next;
    })
    return node.next;
};

// 思路2：
var reverseList = function(head) {
    let [pre, cur] = [null, head];
    while(cur) {
        let tmp = cur.next; //临时存储下一个节点
        cur.next = pre; // 反转链表
        pre = cur; // 接收链表反转的结果
        cur = tmp; // 接回临时存储的后续内容
    }
    return pre;
};

// 思路3:
var reverseList = function(head) {
    if(!head || !head.next) return head;
    let next = head.next; // next节点，反转后是最后一个节点
    let reverseListNode = reverseList(next);
    head.next = null; // 裁减 head
    next.next = head; // 尾接
    return reverseListNode;
};
```

## 209. 长度最小的子数组

```txt
滑动窗口法，时间复杂度O(N)，空间复杂度O(1)
```

```js
var minSubArrayLen = function(s, nums) {
    let minLen = Infinity;
    let i = 0;
    let j = 0;
    let sum = 0;
    while(j < nums.length) {
        sum += nums[j];
        while(sum >= s) {
            minLen = Math.min(minLen, j-i+1);
            sum -= nums[i];
            i++;
        }
        j++;
    }
    return minLen === Infinity ? 0 : minLen;
};
```

## 215. 数组中的第K个最大元素

```txt
TopK问题：
思路1：排序，取第k个
思路2：构造前 k 个最大元素小顶堆，取堆顶
思路3:快排
```

```js
// 思路1，时间复杂度O(N^2)
var findKthLargest = function(nums, k) {
    nums.sort((a,b) => b-a);
    return nums[k-1];
};

// 思路2
var findKthLargest = function(nums, k) {
    // 从 nums 中取出前 k 个数，构建一个小顶堆
    let heap = [,], i = 0
    while(i < k) {
       heap.push(nums[i++])
    }
    buildHeap(heap, k)
    // 从 k 位开始遍历数组
    for(let i = k; i < nums.length; i++) {
        if(heap[1] < nums[i]) {
            // 替换并堆化
            heap[1] = nums[i]
            heapify(heap, k, 1)
        }
    }
    // 返回堆顶元素
    return heap[1]
};

// 原地建堆，从后往前，自上而下式建小顶堆
let buildHeap = (arr, k) => {
    if(k === 1) return
    // 从最后一个非叶子节点开始，自上而下式堆化
    for(let i = Math.floor(k/2); i>=1 ; i--) {
        heapify(arr, k, i)
    }
}

// 堆化
let heapify = (arr, k, i) => {
    // 自上而下式堆化
    while(true) {
        let minIndex = i
        if(2*i <= k && arr[2*i] < arr[i]) {
            minIndex = 2*i
        }
        if(2*i+1 <= k && arr[2*i+1] < arr[minIndex]) {
            minIndex = 2*i+1
        }
        if(minIndex !== i) {
            swap(arr, i, minIndex)
            i = minIndex
        } else {
            break
        }
    }
}

// 交换
let swap = (arr, i , j) => {
    let temp = arr[i]
    arr[i] = arr[j]
    arr[j] = temp
}

// 思路3
let findKthLargest = function(nums, k) {
    return quickSelect(nums, nums.length - k)
};

let quickSelect = (arr, k) => {
  return quick(arr, 0 , arr.length - 1, k)
}

let quick = (arr, left, right, k) => {
  let index;
  if(left < right) {
    // 划分数组
    index = partition(arr, left, right)
    // Top k
    if(k === index) {
        return arr[index]
    } else if(k < index) {
        // Top k 在左边
        return quick(arr, left, index-1, k)
    } else {
        // Top k 在右边
        return quick(arr, index+1, right, k)
    }
  }
  return arr[left]
}

let partition = (arr, left, right) => {
  // 取中间项为基准
  var datum = arr[Math.floor(Math.random() * (right - left + 1)) + left],
      i = left,
      j = right
  // 开始调整
  while(i < j) {
    // 左指针右移
    while(arr[i] < datum) {
      i++
    }
    // 右指针左移
    while(arr[j] > datum) {
      j--
    }
    // 交换
    if(i < j) {
      [arr[i], arr[j]] = [arr[j], arr[i]];
    }

    // 当数组中存在重复数据时，即都为datum，但位置不同
    // 继续递增i，防止死循环
    if(arr[i] === arr[j] && i !== j) {
        i++
    }
  }
  return i
}
```

## 234. 回文链表

```txt
思路1：
用一个数组存储每个节点的值，时间复杂度O(N)，空间复杂度O(N)

思路2:进阶：你能否用 O(n) 时间复杂度和 O(1) 空间复杂度解决此题？
快慢指针 + 逆反链表：快指针每次两步，慢指针一步，在慢指针走的时候将每一步的指针反向，例如：1->2->4->2->1
  慢指针：2->4->2->1 快指针：4->2->1 逆反指针：1->null
  慢指针：4->2->1    快指针：1       逆反指针：2->1
这里注意处理一下链表个数为奇数的情况：需要继续让慢指针向后走一步
最后同时遍历慢指针和逆反指针，判断是否相等即可。
```

```js
// 思路1
var isPalindrome = function(head) {
    let arr = [];
    let p = head;
    while(p) {
        arr.push(p.val);
        p = p.next;
    }
    return arr.join('') === arr.reverse().join('');
};

// 思路2
var isPalindrome = function(head) {
    let mid = head;
    let reversed = null;
    let pre = null;
    while(head && head.next) {
        // 先把mid节点保存一下
        pre = mid;
        head = head.next.next;// 走两步
        mid = mid.next; // 走一步
        // reversed是上一轮遍历的pre节点，将指针反向：pre->pre.next变成pre.next->pre
        pre.next = reversed;
        reversed = pre;
    }
    if(head) { // 奇数的情况，要将mid再往后移动一位
        mid = mid.next;
    }
    while(mid && reversed) {
        if(mid.val !== reversed.val) {
            return false;
        }
        mid = mid.next;
        reversed = reversed.next;
    }
    return true;
};
```

## 876. 链表的中间结点

```txt
思路1:
两次遍历，第一次遍历获取单链表的长度，第二次只要遍历到中间即可。

思路2:
一次遍历：快慢指针，慢指针一次走一步，快指针一次走两步。
```

```js
// 两次遍历
var middleNode = function(head) {
    let p = head;
    let len = 0;
    while(p) {
        len++;
        p = p.next;
    }
    len = len % 2 === 0 ? len / 2 + 1 : Math.floor(len / 2) + 1;
    while(len > 1) { // 这里注意是大于1，比如len=3，head只需要往后移两次，1->2,2->3
        head = head.next;
        len--;
    }
    return head;
};

// 快慢指针
var middleNode = function(head) {
    let slow = head, fast = head;
    while(fast && fast.next) {
        slow = slow.next;
        fast = fast.next.next;
    }
    return slow;
};
```
