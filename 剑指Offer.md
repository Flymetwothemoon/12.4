
# 2022.12.4

## 轮转数组

中等

给你一个数组，将数组中的元素向右轮转 `k` 个位置，其中 `k` 是非负数。

**示例 1:**

```
输入: nums = [1,2,3,4,5,6,7], k = 3
输出: [5,6,7,1,2,3,4]
解释:
向右轮转 1 步: [7,1,2,3,4,5,6]
向右轮转 2 步: [6,7,1,2,3,4,5]
向右轮转 3 步: [5,6,7,1,2,3,4]
```

**示例 2:**

```
输入：nums = [-1,-100,3,99], k = 2
输出：[3,99,-1,-100]
解释: 
向右轮转 1 步: [99,-1,-100,3]
向右轮转 2 步: [3,99,-1,-100]
```

```java
class Solution {

  public void rotate(int[] nums, int k) {

   int nums1[] = new int[nums.length];

   k = k%nums.length;

​    for(int i = 0;i<nums.length;i++){

​      nums1[i]= nums[i];

​    }

​    int w =0;

​    for(int i = 0;i+k<nums.length;i++){

​      nums[i+k] = nums1[i]; 

​      w++;

​    }

​    for(int i = 0;i<nums.length-w;i++){

​      nums[i] = nums1[w+i];

​    }

}

}
```

## 28. 找出字符串中第一个匹配项的下标

给你两个字符串 `haystack` 和 `needle` ，请你在 `haystack` 字符串中找出 `needle` 字符串的第一个匹配项的下标（下标从 0 开始）。如果 `needle` 不是 `haystack` 的一部分，则返回 `-1` 。

 

**示例 1：**

```
输入：haystack = "sadbutsad", needle = "sad"
输出：0
解释："sad" 在下标 0 和 6 处匹配。
第一个匹配项的下标是 0 ，所以返回 0 。
```

**示例 2：**

```
输入：haystack = "leetcode", needle = "leeto"
输出：-1
解释："leeto" 没有在 "leetcode" 中出现，所以返回 -1 。
```



```java
class Solution {
    public int strStr(String haystack, String needle) {
         char[]c = needle.toCharArray();
        int cnt_0 ;
        int w =0;
        int sum[] = new int[10000];
        sum[0]=-1;
       for (int i = 0; i < haystack.length(); i++) {
            cnt_0 = 0;
            for (int j = i; j < haystack.length(); j++) {
//            int k = i;
                if (haystack.charAt(j) == c[cnt_0]) {
                    cnt_0++;


                } else {
                    cnt_0 = 0;
                    if (haystack.charAt(j) == c[cnt_0]) {

                        cnt_0++;
                    }

                }
                if (cnt_0 == needle.length()) {
                    sum[w] = j - needle.length() + 1;
                    w++;
                    cnt_0 = 0;

                }

            }


        } return sum[0];
    }
    }
```
