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
