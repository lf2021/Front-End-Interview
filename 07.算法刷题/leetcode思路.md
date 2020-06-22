# leetcode

前300道题目（不包括困难级别题目）思路，仅供参考

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

## 56. 合并区间

```txt
贪心算法。
先排序，将二维数组中的一维数组升序；结果放在List<int[]> res中。比较，当前数组cur，前一个数组pre，若cur[0]>pre[1]，则不合并，否则合并(对res中最近放进的数组进行操作：`res.get(res.size()-1)[1]=Math.max(cur[1], res.get(res.size()-1)[1]`)
```

## 75. 颜色分类

```txt
本问题被称为荷兰国旗问题，其主要思想是给每个数字设定一种颜色，并按照荷兰国旗颜色的顺序进行调整。0、1、2三个数字分别代表红色、白色和蓝色。一样的颜色放在一起，不同颜色按照数字大小排序。

方法一:
三指针（也有分区快排的意思），用三个指针（p0, p2 和curr）来分别追踪0的最右边界，2的最左边界和当前考虑的元素。沿着数组移动 curr 指针，若nums[curr] = 0，则将其与 nums[p0]互换；若 nums[curr] = 2 ，则与 nums[p2]互换。初始化0的最右边界：p0 = 0。在整个算法执行过程中 nums[idx < p0] = 0。初始化2的最左边界 ：p2 = n - 1。在整个算法执行过程中 nums[idx > p2] = 2。初始化当前考虑的元素序号 ：curr = 0. While curr <= p2 :若 nums[curr] = 0 ：交换第 curr个 和 第p0个 元素，并将指针都向右移；若 nums[curr] = 2 ：交换第 curr个和第 p2个元素，并将 p2指针左移；若 nums[curr] = 1 ：将指针curr右移。
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

## 147. 对链表进行插入排序

```txt
用三个指针，pre指着已排序链表中的起始结点，end指着已排序链表的最后结点，取需要排序链表中的结点cur，若是cur.val > end.val，直接追加，否则从pre开始找到最后一个小于cur.val，插入
```

## 148. 排序链表

使用归并排序

## 179. 最大数

```txt
把数组的元素转成字符串，比较。使用自定义类（实现了接口Comparator,重写了compare(String a,String b)方法，`return (b+a).compareTo((a+b));`)，即a+b > b+a,我们把a排在b前面。使用`Arrays.sort(asStrs, new LargerNumberComparator());`，将字符串数组asStrs排序，最后将这个数组中的元素连接起来即可。
```

## 220. 存在重复元素 III

```txt
使用二叉搜索树， TreeSet
```

## 274. H 指数

```txt
将输入数组citations降序，再遍历，找到满足条件`citations[i]>i` 的最大i，返回i+1，即是h指数
```

## 121. 买卖股票的最佳时

```txt
暴力法，不断比较该值后面所有的元素，依此更新最大值，返回最大值；暴力法的优化，可以只比较现在值之前的最小值，以省去内层循环；

动态规划，k=1，题意规定只能完成一笔交易，简化的(优化存储空间的)状态转移方程为 dp_i_0 = Math.max(dp_i_0, dp_i_1 + prices[i]); 和 dp_i_1 = Math.max(dp_i_1, -prices[i]);
```

## 122. 买卖股票的最佳时机 II

```txt
动态规划和上题一致，只不过k=+infinity。简化的(优化存储空间的)状态转移方程为
int temp=dp_i_0;  dp_i_0 = Math.max(dp_i_0, dp_i_1 + prices[i]);和 dp_i_1 = Math.max(dp_i_1, temp-prices[i]);
```

## 167. 两数之和 II - 输入有序数组

```txt
两遍hashMap；

双指针，lo从数组中元素最小的位置开始，hi从最大。两个指针位置上的数相加，小于目标，lo++，大于则hi--，相等时返回lo+1和hi+1
```

## 189. 旋转数组

```txt
方法一:
使用System.arraycopy进行数组复制。分两部分，一部分是<=k的，一部分是>k。k等于0或数组长度时，直接返回和；k大于数组长度时，k=k%数组长度

方法二:
使用环状替换。每次跳k个元素进行操作

方法三:
使用反转。首先将所有元素反转。然后反转前 k 个元素，再反转后面 n−k个元素，就能得到想要的结果。
反转的操作：起始位置start,终止位置end，当start < end时，交换两个位置上的元素，start++,end--,重复
```

## 217. 存在重复元素

```txt
方法一:
使用队列。先对数组排序，然后利用队列的先进先出，不断对比当前元素和上一个元素是否相等

方法二:
用哈希表。HashSet(底层是HashMap)，可以null,不保证顺序存储，LinkedHashSet和TreeSet有序
```

## 219. 存在重复元素 II

```txt
利用散结构HashSet。

注意点：
由于两个索引之多相差k，于是当hashset.size()>k时就删除旧内容
```

## 242. 有效的字母异位词

```txt
方法一:
先排序，再对比即可，用Arrays.equals(),或者循环逐个对比。

方法二:
哈希表，用一个长度为26的数组来作计数器，第一个字符串s生成的字符数组遍历，计数器对应加1，counter[s.charAt(i) - 'a']++;另一个字符串t生成的字符数组遍历，计数器减1，counter[t.charAt(i) - 'a']--;。当最后计数器中含有不为0的元素，说明两个字符数组不一样，即两个字符串不一样。
```

## 268. 缺失数字

```txt
方法一:
排序后操作 O(nlog⁡n)

方法二:
哈希表，时间复杂度 O(n)

方法三:
位运算,进行两次完全相同的异或运算会得到原来的数，因此我们可以通过异或运算找到缺失的数字。时间复杂度 O(n)

方法四:
数学方法。时间复杂度同上。直接高斯求和0~n，然后将数组所有数求和，相减就得到了缺少的数字了
```

## 283. 移动零

```txt
方法一:
双指针，定义两个指针i,j，然后遍历数组，i跟j同时往前走，当遇到0时j停下，i继续往前走。当nums[i]不为0时则将num[i]的元素赋给j的位置，j++,nums[i]被赋值为0。

方法二:
覆盖的写法，先将不为0的数往前放，next表示索引，当所有不为0的都遍历后，我们把next~len之间的数组元素全设为0。
```
