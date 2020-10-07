# 剑指 offer

```js
牛客链接地址：https://www.nowcoder.com/ta/coding-interviews

全文 67 道算法题，涉及一些基本的数据结构与算法。
```

- [1.二维数组中的查找](#1%e4%ba%8c%e7%bb%b4%e6%95%b0%e7%bb%84%e4%b8%ad%e7%9a%84%e6%9f%a5%e6%89%be)
- [2.替换空格](#2%e6%9b%bf%e6%8d%a2%e7%a9%ba%e6%a0%bc)
- [3.从尾到头打印链表](#3%e4%bb%8e%e5%b0%be%e5%88%b0%e5%a4%b4%e6%89%93%e5%8d%b0%e9%93%be%e8%a1%a8)
- [4.重建二叉树](#4%e9%87%8d%e5%bb%ba%e4%ba%8c%e5%8f%89%e6%a0%91)
- [5.用两个栈实现队列](#5%e7%94%a8%e4%b8%a4%e4%b8%aa%e6%a0%88%e5%ae%9e%e7%8e%b0%e9%98%9f%e5%88%97)
- [6.旋转数组的最小数字](#6%e6%97%8b%e8%bd%ac%e6%95%b0%e7%bb%84%e7%9a%84%e6%9c%80%e5%b0%8f%e6%95%b0%e5%ad%97)
- [7.斐波那契数列](#7%e6%96%90%e6%b3%a2%e9%82%a3%e5%a5%91%e6%95%b0%e5%88%97)
- [8.跳台阶](#8%e8%b7%b3%e5%8f%b0%e9%98%b6)
- [9.变态跳台阶](#9%e5%8f%98%e6%80%81%e8%b7%b3%e5%8f%b0%e9%98%b6)
- [10.矩形覆盖](#10%e7%9f%a9%e5%bd%a2%e8%a6%86%e7%9b%96)
- [11.二进制中 1 的个数](#11%e4%ba%8c%e8%bf%9b%e5%88%b6%e4%b8%ad-1-%e7%9a%84%e4%b8%aa%e6%95%b0)
- [12.数值的整数次方](#12%e6%95%b0%e5%80%bc%e7%9a%84%e6%95%b4%e6%95%b0%e6%ac%a1%e6%96%b9)
- [13.调整数组顺序使奇数位于偶数前面](#13%e8%b0%83%e6%95%b4%e6%95%b0%e7%bb%84%e9%a1%ba%e5%ba%8f%e4%bd%bf%e5%a5%87%e6%95%b0%e4%bd%8d%e4%ba%8e%e5%81%b6%e6%95%b0%e5%89%8d%e9%9d%a2)
- [14.链表中倒数第 k 个结点](#14%e9%93%be%e8%a1%a8%e4%b8%ad%e5%80%92%e6%95%b0%e7%ac%ac-k-%e4%b8%aa%e7%bb%93%e7%82%b9)
- [15.反转链表](#15%e5%8f%8d%e8%bd%ac%e9%93%be%e8%a1%a8)
- [16.合并两个排序的链表](#16%e5%90%88%e5%b9%b6%e4%b8%a4%e4%b8%aa%e6%8e%92%e5%ba%8f%e7%9a%84%e9%93%be%e8%a1%a8)
- [17.树的子结构](#17%e6%a0%91%e7%9a%84%e5%ad%90%e7%bb%93%e6%9e%84)
- [18.二叉树的镜像](#18%e4%ba%8c%e5%8f%89%e6%a0%91%e7%9a%84%e9%95%9c%e5%83%8f)
- [19.顺时针打印矩阵](#19%e9%a1%ba%e6%97%b6%e9%92%88%e6%89%93%e5%8d%b0%e7%9f%a9%e9%98%b5)
- [20.包含 min 函数的栈](#20%e5%8c%85%e5%90%ab-min-%e5%87%bd%e6%95%b0%e7%9a%84%e6%a0%88)
- [21.栈的压入、弹出序列](#21%e6%a0%88%e7%9a%84%e5%8e%8b%e5%85%a5%e5%bc%b9%e5%87%ba%e5%ba%8f%e5%88%97)
- [22.从上往下打印二叉树](#22%e4%bb%8e%e4%b8%8a%e5%be%80%e4%b8%8b%e6%89%93%e5%8d%b0%e4%ba%8c%e5%8f%89%e6%a0%91)
- [23.二叉搜索树的后序遍历序列](#23%e4%ba%8c%e5%8f%89%e6%90%9c%e7%b4%a2%e6%a0%91%e7%9a%84%e5%90%8e%e5%ba%8f%e9%81%8d%e5%8e%86%e5%ba%8f%e5%88%97)
- [24.二叉树中和为某一值的路径](#24%e4%ba%8c%e5%8f%89%e6%a0%91%e4%b8%ad%e5%92%8c%e4%b8%ba%e6%9f%90%e4%b8%80%e5%80%bc%e7%9a%84%e8%b7%af%e5%be%84)
- [25.复杂链表的复制](#25%e5%a4%8d%e6%9d%82%e9%93%be%e8%a1%a8%e7%9a%84%e5%a4%8d%e5%88%b6)
- [26.二叉搜索树与双向链表](#26%e4%ba%8c%e5%8f%89%e6%90%9c%e7%b4%a2%e6%a0%91%e4%b8%8e%e5%8f%8c%e5%90%91%e9%93%be%e8%a1%a8)
- [27.字符串的排列](#27%e5%ad%97%e7%ac%a6%e4%b8%b2%e7%9a%84%e6%8e%92%e5%88%97)
- [28.数组中出现次数超过一半的数字](#28%e6%95%b0%e7%bb%84%e4%b8%ad%e5%87%ba%e7%8e%b0%e6%ac%a1%e6%95%b0%e8%b6%85%e8%bf%87%e4%b8%80%e5%8d%8a%e7%9a%84%e6%95%b0%e5%ad%97)
- [29.最小的 K 个数](#29%e6%9c%80%e5%b0%8f%e7%9a%84-k-%e4%b8%aa%e6%95%b0)
- [30.连续子数组的最大和](#30%e8%bf%9e%e7%bb%ad%e5%ad%90%e6%95%b0%e7%bb%84%e7%9a%84%e6%9c%80%e5%a4%a7%e5%92%8c)
- [31.整数中 1 出现的次数（从 1 到 n 整数中 1 出现的次数）](#31%e6%95%b4%e6%95%b0%e4%b8%ad-1-%e5%87%ba%e7%8e%b0%e7%9a%84%e6%ac%a1%e6%95%b0%e4%bb%8e-1-%e5%88%b0-n-%e6%95%b4%e6%95%b0%e4%b8%ad-1-%e5%87%ba%e7%8e%b0%e7%9a%84%e6%ac%a1%e6%95%b0)
- [32.把整数排成最小的数](#32%e6%8a%8a%e6%95%b4%e6%95%b0%e6%8e%92%e6%88%90%e6%9c%80%e5%b0%8f%e7%9a%84%e6%95%b0)
- [33.丑数](#33%e4%b8%91%e6%95%b0)
- [34.第一次只出现一次的字符](#34%e7%ac%ac%e4%b8%80%e6%ac%a1%e5%8f%aa%e5%87%ba%e7%8e%b0%e4%b8%80%e6%ac%a1%e7%9a%84%e5%ad%97%e7%ac%a6)
- [35.数组中的逆序对](#35%e6%95%b0%e7%bb%84%e4%b8%ad%e7%9a%84%e9%80%86%e5%ba%8f%e5%af%b9)
- [36.两个链表的第一个公共结点](#36%e4%b8%a4%e4%b8%aa%e9%93%be%e8%a1%a8%e7%9a%84%e7%ac%ac%e4%b8%80%e4%b8%aa%e5%85%ac%e5%85%b1%e7%bb%93%e7%82%b9)
- [37.数字在排序数组中出现的次数](#37%e6%95%b0%e5%ad%97%e5%9c%a8%e6%8e%92%e5%ba%8f%e6%95%b0%e7%bb%84%e4%b8%ad%e5%87%ba%e7%8e%b0%e7%9a%84%e6%ac%a1%e6%95%b0)
- [38.二叉树的深度](#38%e4%ba%8c%e5%8f%89%e6%a0%91%e7%9a%84%e6%b7%b1%e5%ba%a6)
- [39.平衡二叉树](#39%e5%b9%b3%e8%a1%a1%e4%ba%8c%e5%8f%89%e6%a0%91)
- [40.数组中只出现一次的数字](#40%e6%95%b0%e7%bb%84%e4%b8%ad%e5%8f%aa%e5%87%ba%e7%8e%b0%e4%b8%80%e6%ac%a1%e7%9a%84%e6%95%b0%e5%ad%97)
- [41.和为 S 的连续正数序列](#41%e5%92%8c%e4%b8%ba-s-%e7%9a%84%e8%bf%9e%e7%bb%ad%e6%ad%a3%e6%95%b0%e5%ba%8f%e5%88%97)
- [42.和为 S 的两个数字](#42%e5%92%8c%e4%b8%ba-s-%e7%9a%84%e4%b8%a4%e4%b8%aa%e6%95%b0%e5%ad%97)
- [43.左旋转字符串](#43%e5%b7%a6%e6%97%8b%e8%bd%ac%e5%ad%97%e7%ac%a6%e4%b8%b2)
- [44.翻转单词顺序列](#44%e7%bf%bb%e8%bd%ac%e5%8d%95%e8%af%8d%e9%a1%ba%e5%ba%8f%e5%88%97)
- [45.扑克牌顺子](#45%e6%89%91%e5%85%8b%e7%89%8c%e9%a1%ba%e5%ad%90)
- [46.孩子们的游戏（圈中最后剩下的数）](#46%e5%ad%a9%e5%ad%90%e4%bb%ac%e7%9a%84%e6%b8%b8%e6%88%8f%e5%9c%88%e4%b8%ad%e6%9c%80%e5%90%8e%e5%89%a9%e4%b8%8b%e7%9a%84%e6%95%b0)
- [47.求 1+2+3+...+n](#47%e6%b1%82-123n)
- [48.不用加减乘除做加法](#48%e4%b8%8d%e7%94%a8%e5%8a%a0%e5%87%8f%e4%b9%98%e9%99%a4%e5%81%9a%e5%8a%a0%e6%b3%95)
- [49.把字符串转换成整数](#49%e6%8a%8a%e5%ad%97%e7%ac%a6%e4%b8%b2%e8%bd%ac%e6%8d%a2%e6%88%90%e6%95%b4%e6%95%b0)
- [50.数组中重复的数字](#50%e6%95%b0%e7%bb%84%e4%b8%ad%e9%87%8d%e5%a4%8d%e7%9a%84%e6%95%b0%e5%ad%97)
- [51.构建乘积数组](#51%e6%9e%84%e5%bb%ba%e4%b9%98%e7%a7%af%e6%95%b0%e7%bb%84)
- [52.正则表达式匹配](#52%e6%ad%a3%e5%88%99%e8%a1%a8%e8%be%be%e5%bc%8f%e5%8c%b9%e9%85%8d)
- [53.表示数值的字符串](#53%e8%a1%a8%e7%a4%ba%e6%95%b0%e5%80%bc%e7%9a%84%e5%ad%97%e7%ac%a6%e4%b8%b2)
- [54.字符流中第一个不重复的字符](#54%e5%ad%97%e7%ac%a6%e6%b5%81%e4%b8%ad%e7%ac%ac%e4%b8%80%e4%b8%aa%e4%b8%8d%e9%87%8d%e5%a4%8d%e7%9a%84%e5%ad%97%e7%ac%a6)
- [55.链表中环的入口结点](#55%e9%93%be%e8%a1%a8%e4%b8%ad%e7%8e%af%e7%9a%84%e5%85%a5%e5%8f%a3%e7%bb%93%e7%82%b9)
- [56.删除链表中重复的结点](#56%e5%88%a0%e9%99%a4%e9%93%be%e8%a1%a8%e4%b8%ad%e9%87%8d%e5%a4%8d%e7%9a%84%e7%bb%93%e7%82%b9)
- [57.二叉树的下一个结点](#57%e4%ba%8c%e5%8f%89%e6%a0%91%e7%9a%84%e4%b8%8b%e4%b8%80%e4%b8%aa%e7%bb%93%e7%82%b9)
- [58.对称的二叉树](#58%e5%af%b9%e7%a7%b0%e7%9a%84%e4%ba%8c%e5%8f%89%e6%a0%91)
- [59.按之字形顺序打印二叉树](#59%e6%8c%89%e4%b9%8b%e5%ad%97%e5%bd%a2%e9%a1%ba%e5%ba%8f%e6%89%93%e5%8d%b0%e4%ba%8c%e5%8f%89%e6%a0%91)
- [60.把二叉树打印成多行](#60%e6%8a%8a%e4%ba%8c%e5%8f%89%e6%a0%91%e6%89%93%e5%8d%b0%e6%88%90%e5%a4%9a%e8%a1%8c)
- [61. 序列化二叉树](#61-%e5%ba%8f%e5%88%97%e5%8c%96%e4%ba%8c%e5%8f%89%e6%a0%91)
- [62.二叉搜索树的第 k 个结点](#62%e4%ba%8c%e5%8f%89%e6%90%9c%e7%b4%a2%e6%a0%91%e7%9a%84%e7%ac%ac-k-%e4%b8%aa%e7%bb%93%e7%82%b9)
- [63.数据流中的中位数](#63%e6%95%b0%e6%8d%ae%e6%b5%81%e4%b8%ad%e7%9a%84%e4%b8%ad%e4%bd%8d%e6%95%b0)
- [64.滑动窗口的最大值](#64%e6%bb%91%e5%8a%a8%e7%aa%97%e5%8f%a3%e7%9a%84%e6%9c%80%e5%a4%a7%e5%80%bc)
- [65.矩阵中的路径](#65%e7%9f%a9%e9%98%b5%e4%b8%ad%e7%9a%84%e8%b7%af%e5%be%84)
- [66.机器人的运动范围](#66%e6%9c%ba%e5%99%a8%e4%ba%ba%e7%9a%84%e8%bf%90%e5%8a%a8%e8%8c%83%e5%9b%b4)
- [67.剪绳子](#67%e5%89%aa%e7%bb%b3%e5%ad%90)

## 1.二维数组中的查找

> 在一个二维数组中（每个一维数组的长度相同），每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

```js
function Find(target, array) {
  // write code here
  for (let i = array.length - 1; i >= 0; i--) {
    if (array[i][0] <= target) {
      if (array[i].includes(target)) {
        return true;
      }
    }
  }
  return false;
}
```

## 2.替换空格

> 请实现一个函数，将一个字符串中的每个空格替换成“%20”。例如，当字符串为 We Are Happy.则经过替换之后的字符串为 We%20Are%20Happy。

```js
function replaceSpace(str) {
  // write code here
  return str.replace(/\s/g, "%20");
}
```

## 3.从尾到头打印链表

> 输入一个链表，按链表从尾到头的顺序返回一个 ArrayList。

```js
/*function ListNode(x){
    this.val = x;
    this.next = null;
}*/
function printListFromTailToHead(head) {
  // write code here
  let res = [];
  while (head) {
    res.unshift(head.val);
    head = head.next;
  }
  return res;
}
```

## 4.重建二叉树

> 输入某二叉树的前序遍历和中序遍历的结果，请重建出该二叉树。假设输入的前序遍历和中序遍历的结果中都不含重复的数字。例如输入前序遍历序列{1,2,4,7,3,5,6,8}和中序遍历序列{4,7,2,1,5,3,8,6}，则重建二叉树并返回。

```js
/* function TreeNode(x) {
    this.val = x;
    this.left = null;
    this.right = null;
} */

function reConstructBinaryTree(pre, vin) {
  // write code here
  if (!pre.length || !vin.length) return null; // 递归基 写递归一定得先写
  var root = pre[0]; //根节点
  var index = vin.indexOf(root); // 在vin中找到根节点的索引
  var left = vin.slice(0, index); // 左子树的中序
  var right = vin.slice(index + 1); // 右子树的中序
  var node = new TreeNode(root); // 新建一个二叉树
  node.left = reConstructBinaryTree(pre.slice(1, index + 1), left); //左子树的前序和中序
  node.right = reConstructBinaryTree(pre.slice(index + 1), right); //右子树的前序和中序
  return node;
}
```

## 5.用两个栈实现队列

> 用两个栈来实现一个队列，完成队列的 Push 和 Pop 操作。 队列中的元素为 int 类型。

```js
const inStack = [];
const outStack = [];

function push(node) {
  // write code here
  inStack.push(node);
}

function pop() {
  // write code here
  if (outStack.length) {
    return outStack.pop();
  } else {
    while (inStack.length) {
      outStack.push(inStack.pop());
    }
    return outStack.pop();
  }
}
```

## 6.旋转数组的最小数字

> 把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。
> 输入一个非递减排序的数组的一个旋转，输出旋转数组的最小元素。
> 例如数组{3,4,5,1,2}为{1,2,3,4,5}的一个旋转，该数组的最小值为 1。
> NOTE：给出的所有元素都大于 0，若数组大小为 0，请返回 0。
> 方法一：二分查找法

```js
function minNumberInRotateArray(rotateArray) {
  // write code here
  if (!rotateArray.length) return 0;
  var left = 0;
  var right = rotateArray.length - 1;
  while (left + 1 < right) {
    var mid = Math.floor((left + right) / 2);
    if (rotateArray[mid] >= rotateArray[left]) {
      left = mid;
    } else {
      right = mid;
    }
  }
  return rotateArray[right];
}
```

> 方法二：扩展运算符

```js
function minNumberInRotateArray(rotateArray) {
  // write code here
  if (!rotateArray.length) {
    return 0;
  } else {
    return Math.min(...rotateArray);
  }
}
```

## 7.斐波那契数列

> 大家都知道斐波那契数列，现在要求输入一个整数 n，请你输出斐波那契数列的第 n 项（从 0 开始，第 0 项为 0）。(n<=39)
> 方法一：动态规划 DP

```js
function Fibonacci(n) {
  // write code here
  if (n === 0 || n === 1) return n;
  let dp = [0, 1];
  for (let i = 2; i <= n; i++) {
    dp[i] = dp[i - 1] + dp[i - 2];
  }
  return dp[n];
}
```

> 方法二：循环

```js
function Fibonacci(n) {
  // write code here
  if (n == 0 || n == 1) {
    return n;
  }
  let triple = [0, 0, 1];
  for (let i = 2; i <= n; i++) {
    triple[0] = triple[1];
    triple[1] = triple[2];
    triple[2] = triple[0] + triple[1];
  }
  return triple[2];
}
```

> 方法三：递归，不写了，最基本的，运行时间不通过

## 8.跳台阶

> 一只青蛙一次可以跳上 1 级台阶，也可以跳上 2 级。求该青蛙跳上一个 n 级的台阶总共有多少种跳法（先后次序不同算不同的结果）。
> 解题思路：
>
> 这题其实就是在求斐波那契数列。理解起来也很简单。假设跳到 n 级台阶有 f(n)种方法。根据题目，青蛙在跳上 n 级时有 2 种方法：
>
> - 从 n - 1 级跳 1 级上来
> - 从 n - 2 级跳 2 级上来
>
> 青蛙跳到 n- 1 级有 f(n-1)种方法，跳到 n- 2 级有 f(n-2)种方法。所以 f(n) = f(n - 1) + f(n - 2)。这就是斐波那契数列的定义式。

```js
function jumpFloor(number) {
  // write code here
  if (number == 1) {
    return 1;
  }
  if (number == 2) {
    return 2;
  }
  let arr = [0, 1, 2];
  for (let i = 3; i <= number; i++) {
    arr[0] = arr[1];
    arr[1] = arr[2];
    arr[2] = arr[0] + arr[1];
  }
  return arr[2];
}
```

## 9.变态跳台阶

> 一只青蛙一次可以跳上 1 级台阶，也可以跳上 2 级……它也可以跳上 n 级。求该青蛙跳上一个 n 级的台阶总共有多少种跳法。
> 方法一：数学归纳法
> 解题思路：
>
> 假设跳 n 级台阶的跳法数量是 f(n)个。假设跳 n 级台阶的跳法数量是 f(n)个。
>
> 那么根据题意，青蛙可能从 n-1 级直接跳上来，也可能从 n-2 级直接跳上来，依次类推：f(n) = f(n - 1) + f(n - 2) + ... + f(1)
>
> 同理：f(n - 1) = f(n - 2) + f(n - 3) + ... + f(1)
>
> f(n) = 2 \* f(n - 1) = 4 \* f(n - 2) = ... = 2 \^ (n - 1)f(1)
>
> 其中： f(1) = 1

```js
function jumpFloorII(number) {
  // write code here
  return Math.pow(2, number - 1);
}
```

> 方法二：动态归纳 DP

```js
function jumpFloorII(number) {
  // write code here
  if (number === 1 || number === 2) return number;
  let dp = [1, 2];
  for (let i = 2; i < number; i++) {
    dp[i] = dp.reduce((t, v) => t + v) + 1;
  }
  return dp[number - 1];
}
```

## 10.矩形覆盖

> 我们可以用 2 \* 1 的小矩形横着或者竖着去覆盖更大的矩形。请问用 n 个 2 \* 1 的小矩形无重叠地覆盖一个 2 \* n 的大矩形，总共有多少种方法？
>
> 比如 n=3 时，2\*3 的矩形块有 3 种覆盖方法：
>
> ![矩阵覆盖](https://raw.githubusercontent.com/Rana1257/Front-end-Collections/Lee/static/img/矩阵覆盖.png)

```js
function rectCover(number) {
  // write code here
  if (number <= 0) {
    return 0;
  }
  if (number == 1) {
    return 1;
  }
  if (number == 2) {
    return 2;
  }
  let arr = [0, 1, 2];
  for (let i = 3; i <= number; i++) {
    arr[0] = arr[1];
    arr[1] = arr[2];
    arr[2] = arr[0] + arr[1];
  }
  return arr[2];
}
```

## 11.二进制中 1 的个数

> 输入一个整数，输出该数二进制表示中 1 的个数。其中负数用补码表示。
> 解题思路：
>
> 如果一个整数不为 0，那么这个整数至少有一位是 1。如果我们把这个整数减 1，那么原来处在整数最右边的 1 就会变为 0，原来在 1 后面的所有的 0 都会变成 1(如果最右边的 1 后面还有 0 的话)。其余所有位将不会受到影响。
>
> 举个例子：一个二进制数 1100，从右边数起第三位是处于最右边的一个 1。减去 1 后，第三位变成 0，它后面的两位 0 变成了 1，而前面的 1 保持不变，因此得到的结果是 1011.我们发现减 1 的结果是把最右边的一个 1 开始的所有位都取反了。这个时候如果我们再把原来的整数和减去 1 之后的结果做与运算，从原来整数最右边一个 1 那一位开始所有位都会变成 0。如 1100&1011=1000.也就是说，把一个整数减去 1，再和原整数做与运算，会把该整数最右边一个 1 变成 0.那么一个整数的二进制有多少个 1，就可以进行多少次这样的操作。

```js
function NumberOf1(n) {
  // write code here
  let count = 0;
  while (n != 0) {
    count++;
    n = n & (n - 1); // 与操作自动将数转换成二进制
  }
  return count;
}
```

## 12.数值的整数次方

> 给定一个 double 类型的浮点数 base 和 int 类型的整数 exponent。求 base 的 exponent 次方。保证 base 和 exponent 不同时为 0.

```js
function Power(base, exponent) {
  // write code here
  return base ** exponent;
}
```

## 13.调整数组顺序使奇数位于偶数前面

> 输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有的奇数位于数组的前半部分，所有的偶数位于数组的后半部分，并保证奇数和奇数，偶数和偶数之间的相对位置不变。

```js
// 额外空间 时间复杂度：O(n) 空间复杂度：O(n)
function reOrderArray(array) {
  // write code here
  let a1 = [];
  let a2 = [];
  array.forEach((item) => {
    item % 2 ? a1.push(item) : a2.push(item);
  });
  return [...a1, ...a2];
}

// in-place算法
// 用 i 记录奇数的位置，遍历数组 j = 0，碰到奇数将其放到 i 的位置，将 [i, j-1] 的元素往后移，并让 i+1
// 时间复杂度：O(n^2),假设数组中一般偶数在前，一半奇数在后，每次都要移动n/2个元素,是n^2/4  空间复杂度：O(1)
function reOrderArray(array) {
  // write code here
  let i = 0;
  for (let j = 0; j < array.length; j++) {
    let tmp = array[j];
    if (tmp & 1) {
      //奇数
      for (let k = j - 1; k >= i; k--) {
        array[k + 1] = array[k];
      }
      array[i++] = tmp;
    }
  }
  return array;
}
```

## 14.链表中倒数第 k 个结点

> 输入一个链表，输出该链表中倒数第 k 个结点。
> 解题思路 1：
>
> 因为要求链表倒数第 k 个节点，也就是求正数第 length - k 个节点。整体过程如下：
>
> - 链表又是个单链表，并且没有保存长度信息。所以需要循环一次计算 length。
> - 第二次循环找到第 length - k 个节点。
>
> 时间复杂度是 O(N)，需要 2 次循环。

```js
/*function ListNode(x){
    this.val = x;
    this.next = null;
}*/

function FindKthToTail(head, k) {
  // write code here
  let length = 0;
  let node = head;
  while (node) {
    length++;
    node = node.next;
  }
  if (k > length) {
    return null;
  }
  let offset = length - k;
  node = head;
  for (let i = 0; i < offset; i++) {
    node = node.next;
  }
  return node;
}
```

> 解题思路 2：
> 准备两个指针：left（慢）和 right（快）。整体过程如下：
>
> - right 先向右移动 k 位，此时 index(right) - index(left) = k
> - left 和 right 一起向右移动，直到 right 抵达边界
> - 由于 index(right) - index(left) = k，所以 index(left) = index(right) - k = length - k。也就是 left 指针移动到了倒数第 k 个位置
>
> 时间复杂度是 O(N)，但仅需要遍历一次。空间复杂度是 O（1）

```js
/*function ListNode(x){
    this.val = x;
    this.next = null;
}*/

function FindKthToTail(head, k) {
  let right = head;
  for (let i = 0; i < k; i++) {
    if (!right) return null; // 链表长度小于k
    right = right.next;
  }

  let left = head;
  while (right) {
    left = left.next;
    right = right.next;
  }

  return left;
}
```

## 15.反转链表

> 输入一个链表，反转链表后，输出新链表的表头。

```js
/*function ListNode(x){
    this.val = x;
    this.next = null;
}*/
function ReverseList(pHead) {
  // write code here
  let prev = null; // 上一个节点
  while (pHead) {
    curr = pHead; // 当前节点
    pHead = pHead.next;
    curr.next = prev;
    prev = curr;
  }
  return prev;
}
```

## 16.合并两个排序的链表

> 输入两个单调递增的链表，输出两个链表合成后的链表，当然我们需要合成后的链表满足单调不减规则。
> 解题思路：
> 设置一个“哨兵节点”叫 pHead，整体流程如下：
>
> - 如果 pHead1 和 pHead2，均没遍历完：
>
>   - 如果 pHead1.val <= pHead2.val，那么当前 node 的 next 指向 pHead1。并且移动 pHead1 指针。
>
>   - 否则，当前 node 的 next 指向 pHead2，移动 pHead2 指针。
>
>   - 移动 node 指针
>
>   - 继续循环
>
> - 否则，结束循环：
>
>   - 如果 pHead1 未遍历完，node 的 next 指向 pHead1
>
>   - 如果 pHead2 未遍历玩，node 的 next 指向 pHead2
>
> 时间复杂度是 O(N)，空间复杂度是 O(1)。代码如下：

```js
/*function ListNode(x){
    this.val = x;
    this.next = null;
}*/
function Merge(pHead1, pHead2) {
  // write code here
  if (!pHead1) {
    // 如果pHead1链表不存在，就返回pHead2
    return pHead2;
  }
  if (!pHead2) {
    // 如果pHead2链表不存在，就返回pHead1
    return pHead1;
  }

  let pHead = new ListNode(-1); // 新建一个‘哨兵节点’
  let node = pHead; // 头节点的指针

  while (pHead1 && pHead2) {
    // pHead1 和 pHead2 都存在时
    if (pHead1.val <= pHead2.val) {
      node.next = pHead1;
      pHead1 = pHead1.next;
    } else {
      node.next = pHead2;
      pHead2 = pHead2.next;
    }
    node = node.next;
  }

  if (pHead1) {
    // pHead1 链表长度大于 pHead2
    node.next = pHead1;
  }
  if (pHead2) {
    // pHead2 链表长度大于 pHead1
    node.next = pHead2;
  }
  return pHead.next; // pHead是-1，所以是pHead.next
}
```

## 17.树的子结构

> 输入两棵二叉树 A，B，判断 B 是不是 A 的子结构。（ps：我们约定空树不是任意一个树的子结构）

```js
/* function TreeNode(x) {
    this.val = x;
    this.left = null;
    this.right = null;
} */

function HasSubtree(pRoot1, pRoot2) {
  // 当pRoot2的根节点与pRoot1的根节点不同时就需要对pRoot1的左右子树进行遍历
  // write code here
  if (pRoot1 == null || pRoot2 == null) {
    // pRoot1 pRoot2 有一个为null，结构就为false
    return false;
  }
  return (
    judgeSubtree(pRoot1, pRoot2) || // pRoot2是不是pRoot1的子结构
    HasSubtree(pRoot1.left, pRoot2) || // pRoot1的左子树中有没有pRoot2
    HasSubtree(pRoot1.right, pRoot2) // pRoot1的右子树中有没有pRoot2
  );
}
function judgeSubtree(root1, root2) {
  // 对root2进行遍历判断root2 是不是root1 的子结构
  if (!root2) {
    return true;
  }
  if (!root1) {
    return false;
  }
  if (root1.val !== root2.val) {
    return judgeSubtree(root1.left, root2) || judgeSubtree(root1.right, root2);
  }
  return judgeSubtree(root1.left, root2.left) && judgeSubtree(root1.right, root2.right);
}
```

## 18.二叉树的镜像

> 操作给定的二叉树，将其变换为源二叉树的镜像。
>
> ![二叉树的镜像](https://raw.githubusercontent.com/Rana1257/Front-end-Collections/Lee/static/img/二叉树的镜像.png)

```js
/* function TreeNode(x) {
  this.val = x;
  this.left = null;
  this.right = null;
} */

function Mirror(root) {
  // write code here
  if (!root) {
    return;
  }
  [root.left, root.right] = [root.right, root.left];
  Mirror(root.left);
  Mirror(root.right);
  return root;
}
```

## 19.顺时针打印矩阵

> 输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字，例如，如果输入如下 4 X 4 矩阵： 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 则依次打印出数字 1,2,3,4,8,12,16,15,14,13,9,5,6,7,11,10.
>
> 解题思路：
>
> 怎么找到标记点？对于每一层来说，设左上角的元素坐标为 (i, j)，那么右上角的元素坐标为 (i, n - j - 1)，右下角的元素坐标是 (m - i - 1 ,n - j - 1)，左下角的元素坐标是 (m - i - 1, j)。找到标记点后，就是对行/列进行+/-的过程。
> 怎么防止重复遍历？找到四个坐标点后，每一层的遍历可以拆分成 4 个部分。
> ![顺时针打印矩阵](https://raw.githubusercontent.com/Rana1257/Front-end-Collections/Lee/static/img/顺时针打印矩阵.png)

```js
function printMatrix(matrix) {
  // write code here
  let m = matrix.length;
  let n = matrix[0].length; //m和n代表矩阵的行数和列数
  if (!m || !n) {
    return [];
  }
  let res = [];
  let i = 0;
  let j = 0; //(i,j)表示左上角的那个坐标
  while (i <= m - 1 - i && j <= n - 1 - j) {
    for (let col = j; col <= n - 1 - j; col++) {
      res.push(matrix[i][col]); //第一行
    }

    for (let row = i + 1; row <= m - 1 - i; row++) {
      res.push(matrix[row][n - 1 - j]); //最后一列
    }
    if (i < m - i - 1 && j < n - j - 1) {
      for (let col = n - j - 2; col >= j + 1; col--) {
        res.push(matrix[m - i - 1][col]);
      }

      for (let row = m - i - 1; row >= i + 1; row--) {
        res.push(matrix[row][j]);
      }
    }
    i++;
    j++;
  }
  return res;
}
```

## 20.包含 min 函数的栈

> 定义栈的数据结构，请在该类型中实现一个能够得到栈中所含最小元素的 min 函数（时间复杂度应为 O（1））。
>
> 注意：保证测试中不会当栈为空的时候，对栈调用 pop()或者 min()或者 top()方法。

```js
const dataStack = []; // 栈
const minStack = []; // 存储栈中最小的元素

function push(node) {
  // write code here
  dataStack.push(node);
  const length = minStack.length;
  if (!length) {
    minStack.push(node);
  } else if (node <= minStack[length - 1]) {
    //每当push一个node，判断这个node：如果不大于minStack中最后一个值，
    //就存入minStack，等号是为了防止push栈中相同的值
    minStack.push(node);
  }
}
function pop() {
  // write code here
  if (dataStack[dataStack.length - 1] === minStack[minStack.length - 1]) {
    minStack.pop();
  }
  return dataStack.pop();
}
function top() {
  // write code here
  return dataStack[dataStack.length - 1];
}
function min() {
  // write code here
  return minStack[minStack.length - 1];
}
```

## 21.栈的压入、弹出序列

> 输入两个整数序列，第一个序列表示栈的压入顺序，请判断第二个序列是否可能为该栈的弹出顺序。假设压入栈的所有数字均不相等。例如序列 1,2,3,4,5 是某栈的压入顺序，序列 4,5,3,2,1 是该压栈序列对应的一个弹出序列，但 4,3,5,1,2 就不可能是该压栈序列的弹出序列。（注意：这两个序列的长度是相等的）
> 解题思路：
>
> 需要一个辅助栈，来模拟出入栈的过程。算法流程如下：
>
> - 取压入队列的首元素，将其压入辅助栈
> - 检查辅助栈顶元素是否和弹出队列的首元素相等：
>   - 若相等，则辅助栈弹出栈顶元素，弹出队列取出队首元素，重复检查
>   - 若不相等，回到第一步
> - 最后，检查辅助栈和弹出队列是否均为空。
>
> 时间复杂度是 O(N^2)，空间复杂度是 O(N)。

```js
function IsPopOrder(pushV, popV) {
  // write code here
  const stack = [];
  pushV.forEach((item) => {
    if (item === popV[0]) {
      popV.shift();
      while (stack.length && stack[stack.length - 1] === popV[0]) {
        stack.pop();
        popV.shift();
      }
    } else {
      stack.push(item);
    }
  });
  return !stack.length && !popV.length;
}
```

## 22.从上往下打印二叉树

> 从上往下打印出二叉树的每个节点，同层节点从左至右打印。

```js
/* function TreeNode(x) {
    this.val = x;
    this.left = null;
    this.right = null;
} */

function PrintFromTopToBottom(root) {
    // write code here
    if (!root) return false;
    let nodes = [];
    let res = [];
    nodes.push(root)
    while(nodes.length > 0) {
        let node = nodes.shift();
        res.push(node.val);
        node.left && nodes.push(node.left);
        node.right && nodes.push(node.right);
    }
    return res
}
```

## 23.二叉搜索树的后序遍历序列

> 输入一个整数数组，判断该数组是不是某二叉搜索树的后序遍历的结果。如果是则输出 true,否则输出 false。假设输入的数组的任意两个数字都互不相同。

```js
/*
在二叉搜索树中：
1.若任意结点的左子树不空，则左子树上所有结点的值均不大于它的根结点的值。
2. 若任意结点的右子树不空，则右子树上所有结点的值均不小于它的根结点的值。
3.任意结点的左、右子树也分别为二叉搜索树。
*/
function VerifySquenceOfBST(sequence) {
  // write code here
  if (!sequence || !sequence.length) {
    return false;
  }
  return __VerifySquenceOfBST(sequence);
}

function __VerifySquenceOfBST(sequence) {
  const len = sequence.length;
  if (len < 2) return true;
  const root = sequence[len - 1];
  let i = 0;
  for (; i < len - 1 && sequence[i] < root; i++) {} //left的数量是i，0 -> i-1
  for (let j = i; j < len - 1; j++) {
    if (sequence[j] < root) {
      return false;
    }
  }
  return __VerifySquenceOfBST(sequence.slice(0, i)) && __VerifySquenceOfBST(sequence.slice(i, len - 1));
}
```

## 24.二叉树中和为某一值的路径

> 输入一颗二叉树的根节点和一个整数，打印出二叉树中结点值的和为输入整数的所有路径。路径定义为从树的根结点开始往下一直到叶结点所经过的结点形成一条路径。(注意: 在返回值的 list 中，数组长度大的数组靠前)

```js
/* function TreeNode(x) {
    this.val = x;
    this.left = null;
    this.right = null;
} */

function FindPath(root, expectNumber) {
  // write code here
  var result = [];
  if (root === null) {
    return result;
  }
  dfsFind(root, expectNumber, [], 0, result);
  return result;
}

function dfsFind(root, expectNumber, path, sum, result) {
  sum += root.val;
  path.push(root.val);
  if (sum === expectNumber && root.left === null && root.right === null) {
    result.push(path.slice(0)); // 为什么不能直接push(path),因为在深度优先搜索的时候path都是指向的同一个
  }
  if (root.left !== null) {
    dfsFind(root.left, expectNumber, path, sum, result);
  }
  if (root.right !== null) {
    dfsFind(root.right, expectNumber, path, sum, result);
  }
  path.pop();
}
```

## 25.复杂链表的复制

> 输入一个复杂链表（每个节点中有节点值，以及两个指针，一个指向下一个节点，另一个特殊指针指向任意一个节点），返回结果为复制后复杂链表的 head。（注意，输出结果中请不要返回参数中的节点引用，否则判题程序会直接返回空）
> 解题思路：
>
> 按照正常的思路，首先从头到尾遍历链表，拷贝每个节点的 value 和 next 指针。然后从头再次遍历，第二次遍历的目的在于拷贝每个节点的 sibling 指针。
>
> 然而即使找到原节点的 sibling 指针，还是得为了找到复制节点对应的 sibling 指针而再遍历一遍。那么对于 n 个要寻找 sibling 指针的节点，复杂度就是 O(N\*N)。
>
> 显然，为了降低复杂度，必须从第二次遍历着手。这里采用的方法是，在第一次遍历的时候，把 (原节点, 复制节点) 作为映射保存在表中。那么第二次遍历的时候，就能在 O(1) 的复杂度下立即找到原链上 sibling 指针在复制链上对应的映射。

```js
/*function RandomListNode(x){
    this.label = x;
    this.next = null;
    this.random = null;
}*/

function Clone(pHead) {
  // write code here
  if (!pHead || !pHead.next) {
    return pHead;
  }
  const map = new Map();
  let node = pHead;
  const newHead = new RandomListNode(node.label);
  let newNode = newHead;
  map.set(node, newNode);

  while (node.next) {
    newNode.next = new RandomListNode(node.next.label);
    node = node.next;
    newNode = newNode.next;
    map.set(node, newNode);
  }
  newNode = newHead;
  node = pHead;
  while (newNode) {
    newNode.random = map.get(node.random);
    newNode = newNode.next;
    node = node.next;
  }
  return newHead;
}
```

## 26.二叉搜索树与双向链表

> 输入一棵二叉搜索树，将该二叉搜索树转换成一个排序的双向链表。要求不能创建任何新的结点，只能调整树中结点指针的指向。
> 方法一：递归+数组
>
> 解题思路：
>
> - 中序遍历一遍二叉搜索树，将节点保存在一个数组中。
> - 遍历数组，更改每个节点的 left 和 right
> - 返回数组第一个元素
>   时间复杂度是 O(N)，空间复杂度是 O(N)。相较于方法二，多开辟了 O(N)的数组空间。

```js
/* function TreeNode(x) {
    this.val = x;
    this.left = null;
    this.right = null;
} */
function Convert(pRootOfTree) {
  // write code here
  if (!pRootOfTree) {
    return null;
  }
  const nodes = [];
  midTravel(pRootOfTree, nodes);
  const len = nodes.length;
  for (let i = 0; i < len; i++) {
    nodes[i].right = nodes[i + 1] || null;
    nodes[i].left = nodes[i - 1] || null;
  }
  return nodes[0];
}

//中序遍历,将所有节点存在nodes中
function midTravel(node, nodes) {
  if (node.left) {
    midTravel(node.left, nodes);
  }
  nodes.push(node);
  if (node.right) {
    midTravel(node.right, nodes);
  }
}
```

> 方法二：一次递归
> 二叉搜索树的性质是：左节点 < 当前节点 < 右节点。转换后的双向链表是有序的，这里采用中序递归遍历保证有序性。
>
> 设计的递归函数返回的是：已转换好的双向链表的尾结点，也就是当前节点的 left 指针应该指向的地方。递归函数的实现思路：
>
> - 检查 left 是否为空，不为空，那么递归调用（传入左子树）
> - 将 left 指针指向已转换好的双向链表的尾结点，并将尾节点的 right 指向当前节点
> - 更新双向链表尾节点（变为当前节点），检查 right 是否为空，不为空，递归调用传入右子树）
> - 返回转换后的双向链表尾节点
>   整个过程的要递归遍历一遍二叉树，时间复杂度是 O(N)，空间复杂度是 O(N)。

```js
/* function TreeNode(x) {
    this.val = x;
    this.left = null;
    this.right = null;
} */

function Convert(pRootOfTree) {
  if (!pRootOfTree) {
    return null;
  }
  __Convert(pRootOfTree, null);
  let node = pRootOfTree;
  while (node.left) {
    node = node.left;
  }
  return node;
}

function __Convert(pRootOfTree, lastNodeInList = null) {
  if (!pRootOfTree) {
    return null;
  }
  // step1:左子树
  if (pRootOfTree.left) {
    lastNodeInList = __Convert(pRootOfTree.left, lastNodeInList);
  }
  // step2:当前节点
  pRootOfTree.left = lastNodeInList;
  if (lastNodeInList) {
    lastNodeInList.right = pRootOfTree;
  }
  // step3:右子树
  lastNodeInList = pRootOfTree;
  if (pRootOfTree.right) {
    lastNodeInList = __Convert(pRootOfTree.right, lastNodeInList);
  }

  return lastNodeInList;
}
```

## 27.字符串的排列

> 输入一个字符串,按字典序打印出该字符串中字符的所有排列。例如输入字符串 abc,则打印出由字符 a,b,c 所能排列出来的所有字符串 abc,acb,bac,bca,cab 和 cba。
>
> 输入描述：输入一个字符串,长度不超过 9(可能有字符重复),字符只包括大小写字母。
> 解题思路：
>
> abc 的所有组合可以这么理解：
>
> 每次取一个字符出来，比如'a'，然后剩下的字符组合成'bc'，'bc'的所有组合可以通过递归来获取，在 bc 的所有组合前面都拼接一个字符'a'；
>
> 再取出字符'b'，剩下的字符拼接成'ac'，同样的方法：'ac'的组合可以通过递归，在'ac'的所有组合前面都拼接一个字符'b'，
>
> 依次类推...
>
> 但是要**注意**：每次取出来的字符不能与前面的字符相同，所有用一个数组 map 来记录每次取出来的值

```js
function Permutation(str) {
  // write code here
  var arr = [];
  if (str.length === 0) return [];
  if (str.length === 1) {
    arr.push(str);
  } else {
    var map = []; //用来判断是不是每次取出来的字符与前面取出来的是否有重复
    for (let i = 0; i < str.length; i++) {
      var s = str[i]; // 索引为i的字符
      if (!map.includes(s)) {
        var st = str.slice(0, i) + str.slice(i + 1); // 剩下的字符拼接成一个新字符
        var a = Permutation(st); // 递归，找出新字符的排列组合
        a.forEach((ele) => arr.push(s + ele));
      }
      map.push(s); //把s加入到map中
    }
  }
  return arr;
}
```

## 28.数组中出现次数超过一半的数字

> 数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。例如输入一个长度为 9 的数组[1,2,3,2,2,2,5,4,2]。由于数字 2 在数组中出现了 5 次，超过数组长度的一半，因此输出 2。如果不存在则输出 0。

```js
function MoreThanHalfNum_Solution(numbers) {
  // write code here
  var len = numbers.length;
  var obj = {};
  numbers.forEach((item) => {
    if (!obj[item]) {
      obj[item] = 1;
    } else {
      obj[item]++;
    }
  });
  for (let key in obj) {
    if (obj[key] > len / 2) {
      return key;
    }
  }
  return 0;
}
```

## 29.最小的 K 个数

> 输入 n 个整数，找出其中最小的 K 个数。例如输入 4,5,1,6,2,7,3,8 这 8 个数字，则最小的 4 个数字是 1,2,3,4,。
> 方法一：快排

```js
function GetLeastNumbers_Solution(input, k) {
  // write code here
  if (k > input.length) return [];
  quickSort(input);
  return input.slice(0, k);
}

function quickSort(input, left = 0, right = input.length - 1) {
  if (left >= right) return;
  var baseId = left;
  var baseVal = input[baseId];
  var i = left;
  var j = right;
  while (i < j) {
    while (j > i && input[j] >= baseVal) {
      j--;
    }
    while (i < j && input[i] <= baseVal) {
      i++;
    }
    [input[i], input[j]] = [input[j], input[i]];
  }
  [input[baseId], input[j]] = [input[j], input[baseId]];
  quickSort(input, left, j - 1);
  quickSort(input, j + 1, right);
  return input;
}
```

> 方法二：冒泡排序

```js
function GetLeastNumbers_Solution(input, k) {
  // write code here
  if (k > input.length) return [];
  for (let j = input.length - 1; j >= input.length - k; j--) {
    for (let i = 0; i < j; i++) {
      if (input[i] < input[i + 1]) {
        [input[i], input[i + 1]] = [input[i + 1], input[i]];
      }
    }
  }
  var res = [];
  while (k > 0) {
    res.push(input.pop());
    k--;
  }
  return res;
}
```

> 方法三：sort 排序

```js
function GetLeastNumbers_Solution(input, k) {
  // write code here
  if (input.length < k) {
    return [];
  }
  input.sort((a, b) => a - b);
  return input.slice(0, k);
}
```

## 30.连续子数组的最大和

> HZ 偶尔会拿些专业问题来忽悠那些非计算机专业的同学。今天测试组开完会后,他又发话了:在古老的一维模式识别中,常常需要计算连续子向量的最大和,当向量全为正数的时候,问题很好解决。但是,如果向量中包含负数,是否应该包含某个负数,并期望旁边的正数会弥补它呢？例如:{6,-3,-2,7,-15,1,2,2},连续子向量的最大和为 8(从第 0 个开始,到第 3 个为止)。给一个数组，返回它的最大连续子序列的和，你会不会被他忽悠住？(子向量的长度至少是 1)

```js
/*
举例：array = [1, -2, 3, 10, -4, 7, 2, -5]
初始化 max = 1, temp = 1
i = 1时， temp = -1, max = 1
i = 2时， temp = 3,  max = 3
i = 3时， temp = 13, max = 13
i = 4时， temp = 9 , max = 13
i = 5时， temp = 16, max = 16
i = 6时， temp = 18, max = 18
i = 7时， temp = 13, max = 18;
*/

function FindGreatestSumOfSubArray(array) {
  // write code here
  var max = array[0],
    temp = array[0];
  for (let i = 1; i < array.length; i++) {
    if (temp <= 0) {
      temp = array[i];
    } else {
      temp += array[i];
    }
    if (temp > max) {
      max = temp;
    }
  }
  return max;
}
```

- 动态规划

```txt
dp[i] 定义为以 nums[i] 结尾的最大子数组的和，状态转移方程：
dp[i] = max{ dp[i-1] + nums[i], nums[i] }     表示要么自成一派，要么和前面的子数组合并
连续子数组的最大和一定是 dp 数组的最大值
```

```js
var maxSubArray = function (nums) {
    let len = nums.length;
    let dp = [];
    dp[0] = nums[0];
    for (let i = 1; i < len; i++) {
        dp[i] = Math.max(dp[i - 1] + nums[i], nums[i]);
    }
    return Math.max(...dp);
};
```

## 31.整数中 1 出现的次数（从 1 到 n 整数中 1 出现的次数）

> 求出 1-13 的整数中 1 出现的次数,并算出 100~1300 的整数中 1 出现的次数？为此他特别数了一下 1-13 中包含 1 的数字有 1、10、11、12、13 因此共出现 6 次,但是对于后面问题他就没辙了。ACMer 希望你们帮帮他,并把问题更加普遍化,可以很快的求出任意非负整数区间中 1 出现的次数（从 1 到 n 中 1 出现的次数）。
> 方法一：对于每个数来说求个位只需对 10 取余(%10)，然后将原数除以 10 取整，再对 10 取余拿到十位...依次类推

```js
function NumberOf1Between1AndN_Solution(n) {
  // write code here
  var count = 0;
  for (let i = n; i > 0; i--) {
    for (let j = i; j > 0; j = parseInt(j / 10)) {
      //对j/10取整
      if (j % 10 === 1) {
        count++;
      }
    }
  }
  return count;
}
```

> 方法二：笨方法，将 1 到 n 转换成字符串拼接起来，计算 1 的个数

```js
function NumberOf1Between1AndN_Solution(n) {
  // write code here
  var str = "";
  for (let i = 0; i <= n; i++) {
    str += i;
  }
  var res = str.split("").filter((ele) => ele === "1");
  return res.length;
}
```

## 32.把整数排成最小的数

> 输入一个正整数数组，把数组里所有数字拼接起来排成一个数，打印能拼接出的所有数字中最小的一个。例如输入数组{3，32，321}，则打印出这三个数字能排成的最小数字为 321323。
> 解题思路：
>
> 将数组中的数字连接起来，排成一个最小的数字。将'大数'往后放'小数'往前放，如何定义'大数'和'小数'？比如说有两个数 a 和 b，如果 ab>ba 则 a 是'大数'b 是'小数'，要排成 ba。
>
> 于是，这道题目变成了一个排序问题，将能把组合出来的数字变大的数字往后排。我们这里需要自己定义一个比大小的比较方法。用冒泡排序，可以解决此题。

```js
function PrintMinNumber(numbers) {
  // write code here
  numbers.sort((a, b) => {
    return "" + a + b > "" + b + a ? 1 : -1; // ab 和 ba ASCII码值大的排在后面
    // return [a,b].join("")-[b,a].join("");
  });
  return numbers.join("");
}
```

## 33.丑数

> 把只包含质因子 2、3 和 5 的数称作丑数（Ugly Number）。例如 6、8 都是丑数，但 14 不是，因为它包含质因子 7。 习惯上我们把 1 当做是第一个丑数。求按从小到大的顺序的第 N 个丑数。
> 解题思路：
>
> 首先从丑数的定义我们知道，一个丑数的因子只有 2,3,5，那么丑数 p = 2 ^ x \* 3 ^ y \* 5 ^ z
>
> 换句话说一个丑数一定由另一个丑数乘以 2 或者乘以 3 或者乘以 5 得到
>
> 那么我们从 1 开始乘以 2,3,5，就得到 2,3,5 三个丑数，在从这三个丑数出发乘以 2,3,5 就得到 4,6,10, 6,9,15, 10,15,25 九个丑数
>
> 因为这 9 个数可能会有重复的，所以从这 9 个丑数中拿出最小的数（要比丑数数组中的数大）加入丑数数组
>
> - (1) 丑数数组 [1]
> - 乘以 2：2
> - 乘以 3：3
> - 乘以 5：5
> - (2) 丑数数组 [1,2]
> - 乘以 2：2 4
> - 乘以 3：3 6
> - 乘以 5：5 10
> - (3) 丑数数组 [1,2,3]
> - 乘以 2：2 4 6
> - 乘以 3：3 6 9
> - 乘以 5：5 10 15
> - (4) 丑数数组 [1,2,3,4]
> - 乘以 2：2 4 6 8
> - 乘以 3：3 6 9 12
> - 乘以 5：5 10 15 20

```js
function GetUglyNumber_Solution(index) {
  // write code here
  if (index === 0) return 0;
  var res = [1];
  while (res.length < index) {
    var n1 = res.map((x) => x * 2).find((x) => x > res[res.length - 1]);
    var n2 = res.map((x) => x * 3).find((x) => x > res[res.length - 1]);
    var n3 = res.map((x) => x * 5).find((x) => x > res[res.length - 1]);
    res.push(Math.min(n1, n2, n3));
  }
  return res[index - 1];
}
```

## 34.第一次只出现一次的字符

> 在一个字符串(0<=字符串长度<=10000，全部由字母组成)中找到第一个只出现一次的字符,并返回它的位置, 如果没有则返回 -1（需要区分大小写）
>
> 解题思路：
>
> 遍历字符串的每一个字符，判断 indexOf 和 lastIndexOf 是不是相同

```js
function FirstNotRepeatingChar(str) {
  // write code here
  for (let i = 0; i < str.length; i++) {
    if (str.indexOf(str[i]) === str.lastIndexOf(str[i])) {
      return i;
    }
  }
  return -1;
}
```

## 35.数组中的逆序对

> 在数组中的两个数字，如果前面一个数字大于后面的数字，则这两个数字组成一个逆序对。输入一个数组,求出这个数组中的逆序对的总数 P。并将 P 对 1000000007 取模的结果输出。 即输出 P%1000000007
> 输入描述:
>
> 题目保证输入的数组中没有的相同的数字
>
> 数据范围：
>
> - 对于%50 的数据,size<=10^4
>
> - 对于%75 的数据,size<=10^5
>
> - 对于%100 的数据,size<=2\*10^5
>   输入：1,2,3,4,5,6,7,0
>
> 输出：7
> 归并排序

```js
function InversePairs(data) {
  if (!data || data.length < 2) return 0;
  let copy = data.slice(),
    count = 0;
  count = mergeSort(data, copy, 0, data.length - 1);
  return count % 1000000007;
}

function mergeSort(data, copy, start, end) {
  if (end === start) return 0;
  let mid = (end - start) >> 1, //这就是除以2的意思
    left = mergeSort(copy, data, start, start + mid),
    right = mergeSort(copy, data, start + mid + 1, end),
    count = 0,
    p = start + mid, //前一个数组的最后一个下标
    q = end, //后一个数组的下标
    copyIndex = end; //辅助数组下标，从最后一个算起
  while (p >= start && q >= start + mid + 1) {
    if (data[p] > data[q]) {
      count += q - start - mid; //索引start+mid+1到q的值都是小于data[p]的，总共是q-(start+mid+1)+1
      copy[copyIndex--] = data[p--];
    } else {
      copy[copyIndex--] = data[q--];
    }
  }
  while (p >= start) {
    copy[copyIndex--] = data[p--];
  }
  while (q >= start + mid + 1) {
    copy[copyIndex--] = data[q--];
  }
  return left + right + count;
}
```

## 36.两个链表的第一个公共结点

> 输入两个链表，找出它们的第一个公共结点。（注意因为传入数据是链表，所以错误测试数据的提示是用其他方式显示的，保证传入数据是正确的）
> 解题思路：
> 首先我们要知道什么是公共结点，两个链表从某一节点开始，他们的 next 都指向同一个结点。但由于是单向链表的结点，每个结点只有一个 next，因此从第一个公共结点开始，之后他们的所有结点都是重合的，不可能再出现分叉。
>
> 双指针法。创建两个指针 p1 和 p2,分别指向两个链表的头结点，然后依次往后遍历。如果某个指针到达末尾，则将该指针指向另一个链表的头结点；如果两个指针所指的结点相同，则循环结束，返回当前指针指向的结点。比如两个链表分别为：1->3->4->5->6 和 2->7->8->9->5->6。短链表的指针 p1 会先到达尾部，然后重新指向长链表头部，当长链表的指针 p2 到达尾部时，重新指向短链表头部，此时 p1 在长链表中已经多走了 k 步(k 为两个链表的长度差值)，p1 和 p2 位于同一起跑线，往后遍历找到相同结点即可。其实该方法主要就是用链表循环的方式替代了长链表指针先走 k 步这一步骤。

```js
/*function ListNode(x){
    this.val = x;
    this.next = null;
}*/

function FindFirstCommonNode(pHead1, pHead2) {
  // write code here
  var p1 = pHead1;
  var p2 = pHead2;
  while (p1 !== p2) {
    p1 = p1 == null ? pHead2 : p1.next;
    p2 = p2 == null ? pHead1 : p2.next;
  }
  return p1;
}
```

## 37.数字在排序数组中出现的次数

> 统计一个数字在排序数组中出现的次数。

```js
function GetNumberOfK(data, k) {
  // write code here
  var count = 0;
  data.forEach((ele) => {
    if (ele == k) {
      count++;
    }
  });
  return count;
}
```

## 38.二叉树的深度

> 输入一棵二叉树，求该树的深度。从根结点到叶结点依次经过的结点（含根、叶结点）形成树的一条路径，最长路径的长度为树的深度。

```js
/* function TreeNode(x) {
    this.val = x;
    this.left = null;
    this.right = null;
} */

function TreeDepth(pRoot) {
  // write code here
  if (pRoot === null) {
    return 0;
  }
  var left = TreeDepth(pRoot.left);
  var right = TreeDepth(pRoot.right);
  return Math.max(left, right) + 1;
}
```

## 39.平衡二叉树

> 输入一棵二叉树，判断该二叉树是否是平衡二叉树。
> 平衡二叉树:它是一棵空树或它的左右两个子树的高度差的绝对值不超过 1，并且左右两个子树都是一棵平衡二叉树。

```js
function IsBalanced_Solution(pRoot) {
  return depth(pRoot) !== -1;
}

// 用递归来判断root是不是平衡二叉树，如果不是则返回最大的深度，如果不是则返回-1
function depth(root) {
  if (root === null) return 0;
  var left = depth(root.left);
  if (left === -1) return -1;
  var right = depth(root.right);
  if (right === -1) return -1;
  if (Math.abs(left - right) > 1) {
    return -1;
  } else {
    return 1 + Math.max(left, right);
  }
}
```

## 40.数组中只出现一次的数字

> 一个整型数组里除了两个数字之外，其他的数字都出现了两次。请写程序找出这两个只出现一次的数字。

```js
function FindNumsAppearOnce(array) {
  // write code here
  // return list, 比如[a,b]，其中ab是出现一次的两个数字
  var list = [];
  array.forEach((item) => {
    if (array.indexOf(item) === array.lastIndexOf(item)) {
      list.push(item);
    }
  });
  return list;
}
```

## 41.和为 S 的连续正数序列

> 小明很喜欢数学,有一天他在做数学作业时,要求计算出 9~16 的和,他马上就写出了正确答案是 100。但是他并不满足于此,他在想究竟有多少种连续的正数序列的和为 100(至少包括两个数)。没多久,他就得到另一组连续正数和为 100 的序列:18,19,20,21,22。现在把问题交给你,你能不能也很快的找出所有和为 S 的连续正数序列? Good Luck!
> 输出描述:
>
> 输出所有和为 S 的连续正数序列。序列内按照从小至大的顺序，序列间按照开始数字从小到大的顺序
> 解题思路：
>
> 因为要求连续的数列和，所以这是一个等差数列，并且我们想到用双指针来做，slow，fast。
>
> 等差数列：current（当前值）=(fast-slow+1)(fast+slow)/2
>
> 初始化 slow=1 和 fast=2.(因为考虑要覆盖到所有情况，所以赋值为两个较小的数)
>
> 只要满足 slow<fast,循环就可进行。
>
> 将 current 和 sum 进行比较
>
> - 若 current==sum,即 slow 和 fast 之间的数满足序列要求，所以遍历 slow 和 fast 之间的所有数，存入一个数组。**之后 slow++**（因为要求的所有的连续正数序列，所以要不断的右移，这步不能少）。
> - current<slow,则表明当前值小于 sum，需要 fast++，
> - current>slow,则表明当前值大于 sum，需要减小当前值，即 slow++；

```js
function FindContinuousSequence(sum) {
  // write code here
  var res = [];
  var slow = 1;
  var fast = 2; //快慢指针
  while (slow < fast) {
    var current = ((fast - slow + 1) * (fast + slow)) / 2;
    if (current === sum) {
      var temp = [];
      for (let i = slow; i <= fast; i++) {
        temp.push(i);
      }
      res.push(temp);
      slow++;
    } else if (current < sum) {
      fast++;
    } else {
      slow++;
    }
  }
  return res;
}
```

## 42.和为 S 的两个数字

> 输入一个递增排序的数组和一个数字 S，在数组中查找两个数，使得他们的和正好是 S，如果有多对数字的和等于 S，输出两个数的乘积最小的。
> 输出描述:
>
> 对应每个测试案例，输出两个数，小的先输出。
> 解题思路：
>
> 千万不要被题目误导了，因为数组是递增的，所有两个数乘积最小一定是两端的数，不会是中间的数，那只要用两个指针 low 和 high，初始，low 指向首部，high 指向尾部，判断：
>
> - 当这两个指针对应的数相加和不为 sum 而且 low 比 high 小的时后，继续判断：
>
>   - 如果和大于 sum，说明 high 指针对应的数太大了，high--，往前找
>   - 如果和小于 sum，说明 low 指针对应的数太小了，low++，往后找
>
> - 当这两个指针对应的数相加和为 sum 时，直接返回这两个数
> - 否则返回空数组，表示不存在

```js
function FindNumbersWithSum(array, sum) {
  // write code here
  var low = 0; //此指针指向第一个数
  var high = array.length - 1; //此指针指向第二个数
  while (array[low] + array[high] !== sum && low < high) {
    if (array[low] + array[high] > sum) {
      high--;
    } else {
      low++;
    }
  }
  if (array[low] + array[high] === sum) {
    return [array[low], array[high]];
  }
  return [];
}
```

## 43.左旋转字符串

> 汇编语言中有一种移位指令叫做循环左移（ROL），现在有个简单的任务，就是用字符串模拟这个指令的运算结果。对于一个给定的字符序列 S，请你把其循环左移 K 位后的序列输出。例如，字符序列 S=”abcXYZdef”,要求输出循环左移 3 位后的结果，即“XYZdefabc”。是不是很简单？OK，搞定它！
> 解题思路：
>
> 主要是注意当 str 不存在或者当左移的位数 n 超过了字符串的长度，返回空字符串即可

```js
function LeftRotateString(str, n) {
  // write code here
  if (!str || n > str.length) return "";
  var n = n % str.length;
  return str.slice(n) + str.slice(0, n);
}
```

## 44.翻转单词顺序列

> 牛客最近来了一个新员工 Fish，每天早晨总是会拿着一本英文杂志，写些句子在本子上。同事 Cat 对 Fish 写的内容颇感兴趣，有一天他向 Fish 借来翻看，但却读不懂它的意思。例如，“student. a am I”。后来才意识到，这家伙原来把句子单词的顺序翻转了，正确的句子应该是“I am a student.”。Cat 对一一的翻转这些单词顺序可不在行，你能帮助他么？

```js
function ReverseSentence(str) {
  // write code here
  var arr = str.split(" ");
  arr.reverse();
  return arr.join(" ");
}
```

## 45.扑克牌顺子

> LL 今天心情特别好,因为他去买了一副扑克牌,发现里面居然有 2 个大王,2 个小王(一副牌原本是 54 张^\_^)...他随机从中抽出了 5 张牌,想测测自己的手气,看看能不能抽到顺子,如果抽到的话,他决定去买体育彩票,嘿嘿！！“红心 A,黑桃 3,小王,大王,方片 5”,“Oh My God!”不是顺子.....LL 不高兴了,他想了想,决定大\小 王可以看成任何数字,并且 A 看作 1,J 为 11,Q 为 12,K 为 13。上面的 5 张牌就可以变成“1,2,3,4,5”(大小王分别看作 2 和 4),“So Lucky!”。LL 决定去买体育彩票啦。 现在,要求你使用这幅牌模拟上面的过程,然后告诉我们 LL 的运气如何， 如果牌能组成顺子就输出 true，否则就输出 false。为了方便起见,你可以认为大小王是 0。
> 解题思路：
>
> 用一个 set 来存放数据，0 不要放进去，需要满足三个条件：
>
> - numbers 数组的长度为 5
> - numbers 数组除 0 外不能有重复的数
> - set 中最大的数与最小的数之差必须在 5 以内

```js
function IsContinuous(numbers) {
  // write code here
  if (numbers.length != 5) {
    return false;
  }
  var num = 0; //记录0的个数
  var set = new Set();
  for (let i = 0; i < numbers.length; i++) {
    if (numbers[i] === 0) {
      num++;
    } else {
      set.add(numbers[i]);
    }
  }
  if (num + set.size != 5) {
    //有除0外的重复元素
    return false;
  }
  if (Math.max(...set) - Math.min(...set) < 5) {
    return true;
  }
  return false;
}
```

## 46.孩子们的游戏（圈中最后剩下的数）

> 每年六一儿童节,牛客都会准备一些小礼物去看望孤儿院的小朋友,今年亦是如此。HF 作为牛客的资深元老,自然也准备了一些小游戏。其中,有个游戏是这样的:首先,让小朋友们围成一个大圈。然后,他随机指定一个数 m,让编号为 0 的小朋友开始报数。每次喊到 m-1 的那个小朋友要出列唱首歌,然后可以在礼品箱中任意的挑选礼物,并且不再回到圈中,从他的下一个小朋友开始,继续 0...m-1 报数....这样下去....直到剩下最后一个小朋友,可以不用表演,并且拿到牛客名贵的“名侦探柯南”典藏版(名额有限哦!!^\_^)。请你试着想下,哪个小朋友会得到这份礼品呢？(注：小朋友的编号是从 0 到 n-1)
>
> 如果没有小朋友，请返回-1
> 解题思路：
>
> 用一个数组装上小朋友，[ 0, 1, 2, 3, 4, 5 ]，
> 从-1 开始计数，直到发现那个小朋友，将它出列，将它后面的小朋友放到队伍前，前面的放在后。重新计数。
> 如 m=4 3 出列 新队伍[ 4, 5, 0, 1, 2 ]

```js
function LastRemaining_Solution(n, m) {
  // write code here
  if (n == 0 || m == 0) return -1;
  var i = 0;
  var arr = [];
  while (i < n) {
    arr.push(i++);
  }
  var count = -1;
  while (arr.length > 1) {
    for (let i = 0; i < m; i++) {
      count++;
      if (count == arr.length) {
        count = 0;
      }
    }
    arr = arr.slice(count + 1).concat(arr.slice(0, count));
    count = -1;
  }
  return arr[0];
}
```

## 47.求 1+2+3+...+n

> 求 1+2+3+...+n，要求不能使用乘除法、for、while、if、else、switch、case 等关键字及条件判断语句（A?B:C）。
> 方法一：

```js
function Sum_Solution(n) {
  // write code here
  var sum = Math.pow(n, 2) + n;
  return sum >> 1; //右移一位相当于除以二，相当于parseInt(sum/2)
}
```

> 方法二：递归 + 短路原理

```js
function Sum_Solution(n) {
  // write code here
  var sum = n;
  sum += sum && Sum_Solution(n - 1); //短路原理
  return sum;
}
```

## 48.不用加减乘除做加法

> 写一个函数，求两个整数之和，要求在函数体内不得使用+ - \* /四则运算符号。
> 解题思路：
>
> 使用位运算实现加法
>
> 1. 一位加法
>    举例： 1 + 1 = 2
>
>    ① res1 = 1 ^ 1 = 0
>
>    ② res2 (1 & 1) << 1 = 10
>
>    ③ res1 = res1 ^ res2 = 10
>
>    ④ res2 = (res1 & res2) << 1 = 0
>
> > 两个基本表达式：
> >
> > - 执行加法 x ^ y
> > - 进位操作 ( x & y ) << 1
> >
> > 2. 二位加法
> >    正确的加法计算：11+01 = 100 (3 + 1 = 4)
>
> ① 按位加法： res1 = 11 ^ 01 = 10
>
> ② 与运算进位： res2 = (11 & 01) << 1 = ( 01 ) << 1 = 010
>
> ③ res1 = res1 ^ res2 = 10 ^ 010 = 00
>
> ④ res2 = (10 & 10) << 1 = 100
>
> ⑤ res1 = res1 ^ res2 = 00 ^ 100 = 100
>
> ⑥ res2 = (00 & 100) << 1 = 000
>
> 输出 res1 3. 更高位的加法
> 继续推理可以得出三位数的加法只需重复的计算三次得到第一个表达式的值就是计算出来的结果

```js
function Add(num1, num2) {
  // write code here
  var res1 = num1 ^ num2; //异或 不带进位的加法
  var res2 = (num1 & num2) << 1; //按位与 进位
  while (res2 !== 0) {
    [res1, res2] = [res1 ^ res2, (res1 & res2) << 1];
  }
  return res1;
}
```

## 49.把字符串转换成整数

> 将一个字符串转换成一个整数，要求不能使用字符串转换整数的库函数。 数值为 0 或者字符串不是一个合法的数值则返回 0
> 输入描述：输入一个字符串,包括数字字母符号,可以为空
> 输出描述：如果是合法的数值表达则返回该数字，否则返回 0
> 输入
>
> +2147483647
>
> 1a33
> 输出
>
> 2147483647
>
> 0

```js
function StrToInt(str) {
  // write code here
  var obj = {
    1: 1,
    2: 2,
    3: 3,
    4: 4,
    5: 5,
    6: 6,
    7: 7,
    8: 8,
    9: 9,
    0: 0,
    "-": -1,
    "+": 1,
  };
  for (let i = 0; i < str.length; i++) {
    if (!obj[str[i]]) {
      return 0;
    }
  }
  if (str === "+" || str === "-") return 0;
  var num = str / 1;
  if (num === -2147483649 || num === 2147483648) {
    return 0;
  }
  return num;
}
```

## 50.数组中重复的数字

> 在一个长度为 n 的数组里的所有数字都在 0 到 n-1 的范围内。 数组中某些数字是重复的，但不知道有几个数字是重复的。也不知道每个数字重复几次。请找出数组中任意一个重复的数字。 例如，如果输入长度为 7 的数组{2,3,1,0,2,5,3}，那么对应的输出是第一个重复的数字 2。

```js
function duplicate(numbers, duplication) {
  // write code here
  //这里要特别注意~找到任意重复的一个值并赋值到duplication[0]
  //函数返回True/False
  if (!numbers || numbers.length == 0) {
    return false;
  }
  for (let i = 0; i < numbers.length; i++) {
    var num = numbers[i];
    if (numbers.indexOf(num) !== numbers.lastIndexOf(num)) {
      duplication[0] = num;
      return true;
    }
  }
  return false;
}
```

## 51.构建乘积数组

> 给定一个数组 A[0,1,...,n-1],请构建一个数组 B[0,1,...,n-1],其中 B 中的元素 B[i]=A[0]\*A[1]\*...\*A[i-1]\*A[i+1]\*...\*A[n-1]。不能使用除法。（注意：规定 B[0] = A[1] \* A[2] \* ... \* A[n-1]，B[n-1] = A[0] \* A[1] \* ... \* A[n-2];）

```js
function multiply(array) {
  // write code here
  var b = [];
  array.forEach((ele, index) => {
    var arr = Array.from(array);
    b[index] = arrMul(arr, index);
  });
  return b;
}

//数组除了索引为idx的其余数的乘积和
function arrMul(array, idx) {
  var sum = 1;
  for (let i = 0; i < array.length; i++) {
    if (i == idx) {
      continue;
    } else {
      sum *= array[i];
    }
  }
  return sum;
}
```

## 52.正则表达式匹配

> 请实现一个函数用来匹配包括'.'和'\*'的正则表达式。模式中的字符'.'表示任意一个字符，而'\*'表示它前面的字符可以出现任意次（包含 0 次）。 在本题中，匹配是指字符串的所有字符匹配整个模式。例如，字符串"aaa"与模式"a.a"和"ab\*ac\*a"匹配，但是与"aa.a"和"ab\*a"均不匹配

```js
//s, pattern都是字符串
function match(s, pattern) {
  // write code here
  var reg = new RegExp("^" + pattern + "$", "g");
  return reg.test(s);
}
```

## 53.表示数值的字符串

> 请实现一个函数用来判断字符串是否表示数值（包括整数和小数）。例如，字符串"+100","5e2","-123","3.1416"和"-1E-16"都表示数值。 但是"12e","1a3.14","1.2.3","+-5"和"12e+4.3"都不是。
> 解题思路：
>
> - [-+]? 表示有 0 到 1 个负号或者正号
> - \d\* 表示有 0 到多个数字
> - (?:\.\d\*)? 表示后面是不是紧跟着小数点和数字，(?: …)?表示一个可选的非捕获型分组。
> - (?:[eE][+\\-]?\d+)? 表示匹配一个 e(或 E)、一个可选的正负号以及一个或多个数字。

```js
//s字符串
function isNumeric(s) {
  // write code here
  var reg = /^[+\-]?\d*(?:\.\d*)?(?:[eE][+\-]?\d+)?$/g;
  return reg.test(s);
}
```

## 54.字符流中第一个不重复的字符

> 请实现一个函数用来找出字符流中第一个只出现一次的字符。例如，当从字符流中只读出前两个字符"go"时，第一个只出现一次的字符是"g"。当从该字符流中读出前六个字符“google"时，第一个只出现一次的字符是"l"。
>
> 如果当前字符流没有存在出现一次的字符，返回#字符。

```js
var map = {};
//Init module if you need
function Init() {
  // write code here
  map = {};
}
//Insert one char from stringstream
function Insert(ch) {
  // write code here
  map[ch] = map[ch] ? map[ch] + 1 : 1;
}
//return the first appearence once char in current stringstream
function FirstAppearingOnce() {
  // write code here
  for (let i in map) {
    if (map[i] === 1) {
      return i;
    }
  }
  return "#";
}
```

## 55.链表中环的入口结点

> 给一个链表，若其中包含环，请找出该链表的环的入口结点，否则，输出 null。
> 方法一：
>
> 遍历这个链表，将结点存入数组中，给每次加入的结点做一个判断：是否这个结点已经保存在数组，如果保存过，说明这个结点就是环的入口节点

```js
/*function ListNode(x){
    this.val = x;
    this.next = null;
}*/

function EntryNodeOfLoop(pHead) {
  // write code here
  if (!pHead) return null;
  var arr = [];
  var node = pHead;
  while (node) {
    if (arr.includes(node)) {
      return node;
    }
    arr.push(node);
    node = node.next;
  }
  return null;
}
```

> 方法二：
>
> ![链表中环的入口结点](https://raw.githubusercontent.com/Rana1257/Front-end-Collections/Lee/static/img/链表中环的入口结点.png)
>
> 设置快慢指针，都从链表头出发，快指针每次走两步，慢指针一次走一步，假如有环，一定相遇于环中某点(结论 1)。接着让两个指针分别从相遇点和链表头出发，两者都改为每次走一步，最终相遇于环入口(结论 2)。以下是两个结论证明：
> 两个结论：
>
> 1. 设置快慢指针，假如有环，他们最后一定相遇。
> 2. 两个指针分别从链表头和相遇点继续出发，每次走一步，最后一定相遇与环入口。
>
> **证明结论 1:**
>
> 设置快慢指针 fast 和 slow，fast 每次走两步，slow 每次走一步。假如有环，两者一定会相遇（因为 slow 一旦进环，可看作 fast 在后面追赶 slow 的过程，每次两者都接近一步，最后一定能追上）。
>
> **证明结论 2:**
>
> 设：
>
> - 链表头到环入口长度为--a
> - 环入口到相遇点长度为--b
> - 相遇点到环入口长度为--c
>
> 则：相遇时
>
> **快指针路程=a+(b+c)k+b** ，k>=1 其中 b+c 为环的长度，k 为绕环的圈数（k>=1,即最少一圈，不能是 0 圈，不然和慢指针走的一样长，矛盾）。
>
> **慢指针路程=a+b**
>
> 快指针走的路程是慢指针的两倍，所以：
>
> （a+b）\*2=a+(b+c)k+b
>
> 化简可得：
>
> a=(k-1)(b+c)+c 这个式子的意思是： **链表头到环入口的距离=相遇点到环入口的距离+（k-1）圈环长度。**其中 k>=1,所以 k-1>=0 圈。所以两个指针分别从链表头和相遇点出发，最后一定相遇于环入口。

```js
/*function ListNode(x){
    this.val = x;
    this.next = null;
}*/

function EntryNodeOfLoop(pHead) {
  // write code here
  if (pHead == null) {
    return null;
  }
  if (pHead.next == null) {
    return null;
  }
  var fast = pHead;
  var slow = pHead;
  while (slow != null && fast.next != null) {
    slow = slow.next;
    fast = fast.next.next;
    if (fast == slow) break;
  }

  var p1 = slow;
  var p2 = pHead;
  while (p1 != p2) {
    p1 = p1.next;
    p2 = p2.next;
  }
  return p1;
}
```

## 56.删除链表中重复的结点

> 在一个排序的链表中，存在重复的结点，请删除该链表中重复的结点，重复的结点不保留，返回链表头指针。 例如，链表 1->2->3->3->4->4->5 处理后为 1->2->5
> 解题思路：
>
> 借助一个辅助头节点，设置两个指针 pre 和 cur 分别指向上一个结点和当前结点，当 cur 的值和 cur.next 的值相等就让 cur 往前走，直到不相等的时候退出循环，这时候 cur 还是重复值，令 cur 再往前走一位，调整 pre 和 cur 再次进行判断。
>
> 举例：1->2->3->3->3->4->5 两个指针的走向如下
>
> - -1(辅助头结点)->1->2->3->3->3->4->5
> - -1(pre)->1(cur)->2->3->3->3->4->5
> - -1->1(pre)->2(cur)->3->3->3->4->5
> - -1->1->2(pre)->3(cur)->3->3->4->5
> - -1->1->2(pre)->3->3(cur)->3->4->5
> - -1->1->2(pre)->3->3->3(cur)->4->5
> - -1->1->2(pre)->3->3->3->4(cur)->5
> - -1->1->2(pre)->4(cur)->5
> - -1->1->2->4(pre)->5(cur)

```js
/*function ListNode(x){
    this.val = x;
    this.next = null;
}*/

function deleteDuplication(pHead) {
  // write code here
  if (!pHead) return null;
  var head = new ListNode(-1); //辅助头节点
  head.next = pHead;
  var pre = head;
  var cur = head.next;
  while (cur !== null) {
    if (cur.next !== null && cur.next.val === cur.val) {
      while (cur.next !== null && cur.next.val === cur.val) {
        cur = cur.next;
      }
      cur = cur.next;
      pre.next = cur;
    } else {
      pre = cur;
      cur = cur.next;
    }
  }
  return head.next;
}
```

## 57.二叉树的下一个结点

> 给定一个二叉树和其中的一个结点，请找出中序遍历顺序的下一个结点并且返回。注意，树中的结点不仅包含左右子结点，同时包含指向父结点的指针。
> 解题思路：
>
> 分析二叉树的下一个节点，一共有以下情况：
>
> 1.二叉树为空，则返回空；
>
> 2.有右子树的，那么下个结点就是右子树最左边的点
>
> 3.没有右子树的，也可以分成两类:
>
> - 是父节点左孩子,那么父节点就是下一个节点
> - 是父节点的右孩子,找他的父节点的父节点的父节点...直到当前结点是其父节点的左孩子位置,下一个结点就是当前结点

```js
/*function TreeLinkNode(x){
    this.val = x;
    this.left = null;
    this.right = null;
    this.next = null;
}*/

function GetNext(pNode) {
  // write code here
  if (pNode === null) return null; //空结点
  var p = null;
  if (pNode.right) {
    //有右子树，则下一个结点在右子树最左边的结点
    p = pNode.right;
    while (p.left !== null) {
      p = p.left;
    }
    return p;
  } else {
    //没有右子树
    p = pNode.next;
    if (p && p.right === pNode) {
      while (p.next && p.next.right === p) {
        p = p.next;
      }
      p = p.next;
    }
    return p;
  }
  return null;
}
```

## 58.对称的二叉树

> 请实现一个函数，用来判断一颗二叉树是不是对称的。注意，如果一个二叉树同此二叉树的镜像是同样的，定义其为对称的。空二叉树也是对称的。
> 解题思路：
>
> 空二叉树也是对称的，这是值得注意的点。
>
> 然后将二叉树一层一层比较一下

```js
/* function TreeNode(x) {
    this.val = x;
    this.left = null;
    this.right = null;
} */

function isSymmetrical(pRoot) {
  // write code here
  if (!pRoot) return true; // 注意是true
  return judge(pRoot.left, pRoot.right);
}

function judge(node1, node2) {
  //判断这两个结点以及子节点是否对称
  if (node1 === null && node2 === null) {
    return true;
  } else if (node1 === null || node2 === null) {
    return false;
  }
  if (node1.val !== node2.val) {
    return false;
  } else {
    return judge(node1.left, node2.right) && judge(node1.right, node2.left);
  }
}
```

## 59.按之字形顺序打印二叉树

> 请实现一个函数按照之字形打印二叉树，即第一行按照从左到右的顺序打印，第二层按照从右至左的顺序打印，第三行按照从左到右的顺序打印，其他行以此类推。

输入：
![之字形顺序打印二叉树](https://images.cnblogs.com/cnblogs_com/muzidaitou/1644305/t_200414152956%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20200414232924.png)

输出：
`[[8],[10,6],[5,7,9,11]]`

```js
/* function TreeNode(x) {
    this.val = x;
    this.left = null;
    this.right = null;
} */

function Print(pRoot) {
  // write code here
  if (!pRoot) return [];
  const nodes = []; //结点
  const vals = []; //val
  var flag = true; //true代表顺序打印
  nodes.push(pRoot);
  while (nodes.length) {
    var temp = [];
    // 这里注意要先把nodes的长度赋值给一个变量，因为下面循环中nodes里会添加新的结点
    var len = nodes.length;
    for (let i = 0; i < len; i++) {
      var node = nodes.shift(); // 每次弹出nodes中第一个结点
      flag === true ? temp.push(node.val) : temp.unshift(node.val);
      if (node.left) {
        nodes.push(node.left);
      }
      if (node.right) {
        nodes.push(node.right);
      }
    }
    flag = !flag;
    vals.push(temp);
  }
  return vals;
}
```

## 60.把二叉树打印成多行

> 从上到下按层打印二叉树，同一层结点从左至右输出。每一层输出一行。

```js
/* function TreeNode(x) {
    this.val = x;
    this.left = null;
    this.right = null;
} */

function Print(pRoot) {
  // write code here'
  if (!pRoot) return [];
  const nodes = [];
  const vals = [];
  nodes.push(pRoot);
  while (nodes.length) {
    var len = nodes.length;
    var temp = [];
    for (let i = 0; i < len; i++) {
      var node = nodes.shift();
      temp.push(node.val);
      if (node.left) {
        nodes.push(node.left);
      }
      if (node.right) {
        nodes.push(node.right);
      }
    }
    vals.push(temp);
  }
  return vals;
}
```

## 61. 序列化二叉树

> 请实现两个函数，分别用来序列化和反序列化二叉树
>
> 二叉树的序列化是指：把一棵二叉树按照某种遍历方式的结果以某种格式保存为字符串，从而使得内存中建立起来的二叉树可以持久保存。序列化可以基于先序、中序、后序、层序的二叉树遍历方式来进行修改，序列化的结果是一个字符串，序列化时通过 某种符号表示空节点（#），以 ！ 表示一个结点值的结束（value!）。
>
> 二叉树的反序列化是指：根据某种遍历顺序得到的序列化字符串结果 str，重构二叉树。

```js
/* function TreeNode(x) {
    this.val = x;
    this.left = null;
    this.right = null;
} */

var arr = [];
function Serialize(pRoot) {
  // write code here
  if (!pRoot) {
    arr.push("#");
  } else {
    arr.push(pRoot.val);
    Serialize(pRoot.left);
    Serialize(pRoot.right);
  }
}
function Deserialize(s) {
  // write code here
  if (arr === null) return null;
  if (arr.length < 1) return null;
  var root = null;
  var temp = arr.shift();
  if (typeof temp === "number") {
    root = new TreeNode(temp);
    root.left = Deserialize(arr);
    root.right = Deserialize(arr);
  }
  return root;
}
```

## 62.二叉搜索树的第 k 个结点

> 给定一棵二叉搜索树，请找出其中的第 k 小的结点。例如， （5，3，7，2，4，6，8） 中，按结点数值大小顺序第三小结点的值为 4。
> 解题思路：
>
> 二叉搜索树的特性：左子树 < 根节点 < 右子树
>
> 故只需要找出二叉搜索树的中序，然后找第 k 个结点

```js
/* function TreeNode(x) {
    this.val = x;
    this.left = null;
    this.right = null;
} */
function KthNode(pRoot, k) {
  // write code here
  if (!pRoot || k < 1) {
    return null;
  }
  var res = [];
  function mid(root) {
    if (!root) return null;
    mid(root.left);
    res.push(root);
    mid(root.right);
  }
  mid(pRoot);
  return res[k - 1];
}
```

## 63.数据流中的中位数

> 如何得到一个数据流中的中位数？如果从数据流中读出奇数个数值，那么中位数就是所有数值排序之后位于中间的数值。如果从数据流中读出偶数个数值，那么中位数就是所有数值排序之后中间两个数的平均值。我们使用 Insert()方法读取数据流，使用 GetMedian()方法获取当前读取数据的中位数。

```js
var arr = [];
function Insert(num) {
  // write code here
  arr.push(num);
  let i = arr.length - 1;
  arr.sort((a, b) => a - b);
}
function GetMedian() {
  // write code here
  if (!arr.length) return null;
  var len = arr.length;
  var idx = Math.floor(len / 2);
  if (len % 2 === 1) {
    return arr[idx];
  } else {
    return (arr[idx] + arr[idx - 1]) / 2;
  }
}
```

## 64.滑动窗口的最大值

> 给定一个数组和滑动窗口的大小，找出所有滑动窗口里数值的最大值。例如，如果输入数组{2,3,4,2,6,2,5,1}及滑动窗口的大小 3，那么一共存在 6 个滑动窗口，他们的最大值分别为{4,4,6,6,6,5}； 针对数组{2,3,4,2,6,2,5,1}的滑动窗口有以下 6 个： {[2,3,4],2,6,2,5,1}， {2,[3,4,2],6,2,5,1}， {2,3,[4,2,6],2,5,1}， {2,3,4,[2,6,2],5,1}， {2,3,4,2,[6,2,5],1}， {2,3,4,2,6,[2,5,1]}。

```js
function maxInWindows(num, size) {
  // write code here
  if (size == 0) return [];
  var len = num.length;
  var idx = len - size;
  var res = [];
  for (let i = 0; i <= idx; i++) {
    res.push(Math.max(...num.slice(i, i + size)));
  }
  return res;
}
```

## 65.矩阵中的路径

> 请设计一个函数，用来判断在一个矩阵中是否存在一条包含某字符串所有字符的路径。路径可以从矩阵中的任意一个格子开始，每一步可以在矩阵中向左，向右，向上，向下移动一个格子。如果一条路径经过了矩阵中的某一个格子，则该路径不能再进入该格子。 例如 ​
>
> a s a
> ​
> b f d
> ​
> c c e
>
> e s e
> ​
> 矩阵中包含一条字符串"bcced"的路径，但是矩阵中不包含"abcb"路径，因为字符串的第一个字符 b 占据了矩阵中的第一行第二个格子之后，路径不能再次进入该格子。

```js
function hasPath(matrix, rows, cols, path) {
  // matrix是一个一位数组
  if (!rows || !cols || path.length > rows * cols) return false;
  var k = 0;
  var flag = [];
  for (let i = 0; i < rows; i++) {
    for (let j = 0; j < cols; j++) {
      if (move(matrix, i, j, rows, cols, k, path, flag)) return true;
    }
  }
  return false;
}

function move(matrix, i, j, rows, cols, k, path, flag) {
  //(i,j)代表在矩阵中的位置，k是path字符串的索引，flag是用来标记(i,j)是否已经走过
  var index = i * cols + j; //index表示(i,j)在matrix数组中的索引
  if (i < 0 || i >= rows || j < 0 || j >= cols) return false; //超出边界
  if (path[k] !== matrix[index]) return false; //跟path字符串不相符合
  if (flag[index] === 1) return false; //已经走过
  if (k === path.length - 1) return true;
  走完最后一步;
  flag[index] = 1; //标记已经走过
  if (
    move(matrix, i - 1, j, rows, cols, k + 1, path, flag) ||
    move(matrix, i + 1, j, rows, cols, k + 1, path, flag) ||
    move(matrix, i, j - 1, rows, cols, k + 1, path, flag) ||
    move(matrix, i, j + 1, rows, cols, k + 1, path, flag)
  ) {
    return true;
  }
  flag[index] = 0; //说明此步走的不正确，不标记此步走过
  return false;
}
```

## 66.机器人的运动范围

> 地上有一个 m 行和 n 列的方格。一个机器人从坐标 0,0 的格子开始移动，每一次只能向左，右，上，下四个方向移动一格，但是不能进入行坐标和列坐标的数位之和大于 k 的格子。 例如，当 k 为 18 时，机器人能够进入方格（35,37），因为 3+5+3+7 = 18。但是，它不能进入方格（35,38），因为 3+5+3+8 = 19。请问该机器人能够达到多少个格子？

```js
function movingCount(threshold, rows, cols) {
  // write code here
  function move(i, j, threshold, rows, cols, flag) {
    var index = i * cols + j;
    //无论是广度优先遍历还是深度优先遍历，我们一定要知道的时候遍历一定会有终止条件也就是要能够停止，
    //不然程序就会陷入死循环，这个一定是我们做此类题目必须要注意的地方
    if (i < 0 || i >= rows || j < 0 || j >= cols) return 0; //超出边界
    if (flag[index] === 1) return 0; //已走过
    if (isValid(i, j, threshold) === false) return 0; //不满足行坐标和列坐标的数位之和大于threshold
    flag[index] = 1; //(i, j)满足要求，标记已走过，走过次数+1
    return (
      1 +
      move(i - 1, j, threshold, rows, cols, flag) +
      move(i + 1, j, threshold, rows, cols, flag) +
      move(i, j - 1, threshold, rows, cols, flag) +
      move(i, j + 1, threshold, rows, cols, flag)
    );
  }
  var flag = [];
  return move(0, 0, threshold, rows, cols, flag);
}

function isValid(i, j, threshold) {
  var sum = 0;
  while (i > 0) {
    sum += i % 10;
    i = parseInt(i / 10);
  }
  while (j > 0) {
    sum += j % 10;
    j = parseInt(j / 10);
  }
  if (sum > threshold) {
    return false;
  } else {
    return true;
  }
}
```

## 67.剪绳子

> 给你一根长度为 n 的绳子，请把绳子剪成整数长的 m 段（m、n 都是整数，n>1 并且 m>1），每段绳子的长度记为 k[0],k[1],...,k[m]。请问 k[0]xk[1]x...xk[m]可能的最大乘积是多少？例如，当绳子的长度是 8 时，我们把它剪成长度分别为 2、3、3 的三段，此时得到的最大乘积是 18。
> 输入描述:输入一个数 n，意义见题面。（2 <= n <= 60）
>
> 输出描述:输出答案。
> 输入: 8
>
> 输出: 18
> 方法一：数学公式法（贪婪算法）
> 解题思路：
>
> 绳子长度为 n，分成 m 份，
>
> 假设每份长度为 x，那么 m=n/x;
>
> 那么结果就是 f(x)=x^(n/x)
> ![剪绳子](https://images.cnblogs.com/cnblogs_com/muzidaitou/1644305/o_200418113537%E5%89%AA%E7%BB%B3%E5%AD%90.jpg)
> 所以问题就回到了 n/3 的个数上面
>
> 当 n 能被 3 整除的时候，乘积=n^(n/3)
>
> 当 n 除 3 余 1 的时候，这时候发现多了一个 1，这个 1 是不是很鸡肋，但是把前面的一个 3 拿出来，把这个一个 1 和前面一个 3 分解为 2 和 2，就变大了，所以乘积为 3^(n/3 - 1) \* 4
>
> 当 n 除 3 余 2 的时候，乘积为 n^(n/3) \* 2

```js
function cutRope(number) {
  // write code here
  if (number <= 1) return 0;
  if (number === 2) return 1;
  if (number === 3) return 2;
  var m = number % 3;
  switch (m) {
    case 0:
      return Math.pow(3, number / 3);
    case 1:
      return Math.pow(3, parseInt(number / 3) - 1) * 4;
    case 2:
      return Math.pow(3, parseInt(number / 3)) * 2;
  }
}
```

> 方法二：动态规划 DP

```txt
dp[i]表示长度为i的绳子切成m段之后各段长度的乘积

状态转移方程 dp[i] = max{ dp[i], max{ (i-j)\*j, dp[i-j]\*j } }
要么不减 dp[i]
要么从j开始减，剩余的（i-j）要么不减，要么继续减

时间复杂度: O(N^2)
空间复杂度: O(N)
```

```js
var cuttingRope = function (n) {
  let dp = Array(n + 1).fill(0);
  dp[2] = 1;
  for (let i = 3; i <= n; i++) {
    for (let j = 1; j <= i; j++) {
      dp[i] = Math.max(dp[i], Math.max((i - j) * j, dp[i - j] * j));
    }
  }
  return dp[n];
};
```
