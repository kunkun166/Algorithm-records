##### 2022/4/21

### 计算字符串的数字和

[https://leetcode-cn.com/problems/calculate-digit-sum-of-a-string/](https://leetcode-cn.com/problems/calculate-digit-sum-of-a-string/)

### 题目描述

<font size=2> 给你一个由若干数字（`0` - `9`）组成的字符串 `s` ，和一个整数。<br>如果 `s` 的长度大于 `k` ，则可以执行一轮操作。在一轮操作中，需要完成以下工作：</font>

<font size=2>1、将 `s` **拆分** 成长度为 `k` 的若干 **连续数字组** ，使得前 `k` 个字符都分在第一组，接下来的 `k` 个字符都分在第二组，依此类推。**注意**，最后一个数字组的长度可以小于 `k` 。</font>

<font size=2>2、用表示每个数字组中所有数字之和的字符串来 **替换** 对应的数字组。例如，`"346"` 会替换为 `"13"` ，因为 `3 + 4 + 6 = 13` 。</font>

<font size=2>3、**合并** 所有组以形成一个新字符串。如果新字符串的长度大于 `k` 则重复第一步。</font>

<font size=2>返回在完成所有轮操作后的 `s` 。</font>


<font size=2>示例 1：</font>

```
输入：s = "11111222223", k = 3
输出："135"
解释：
- 第一轮，将 s 分成："111"、"112"、"222" 和 "23" 。
  接着，计算每一组的数字和：1 + 1 + 1 = 3、1 + 1 + 2 = 4、2 + 2 + 2 = 6 和 2 + 3 = 5 。 
  这样，s 在第一轮之后变成 "3" + "4" + "6" + "5" = "3465" 。
- 第二轮，将 s 分成："346" 和 "5" 。
  接着，计算每一组的数字和：3 + 4 + 6 = 13 、5 = 5 。
  这样，s 在第二轮之后变成 "13" + "5" = "135" 。 
现在，s.length <= k ，所以返回 "135" 作为答案。
```

<font size=2>示例 2：</font>

```
输入：s = "00000000", k = 3
输出："000"
解释：
将 "000", "000", and "00".
接着，计算每一组的数字和：0 + 0 + 0 = 0 、0 + 0 + 0 = 0 和 0 + 0 = 0 。 
s 变为 "0" + "0" + "0" = "000" ，其长度等于 k ，所以返回 "000" 。
```

<font size=2>提示：</font>

- `1 <= s.length <= 100`
- `2 <= k <= 100`
- `s 仅由数字（0 - 9）组成。`

### 题解

#### 方法一、StringBuilder

- <font size=2>这道题考察了 Java 中对字符串的处理手段，不得不说 StringBuilder 是真的方便</font>
- <font size=2>首先如果字符串 `s` 长度大于 `k` ，就需要以 `k` 为步长计算这一步中包含的数的和</font>
- <font size=2>计算 `k` 步长内的数字和对应代码里中间两个 `for` 循环，非常巧妙的解决了最后几个数可能不够 `k` 步长的问题</font>
- <font size=2>每计算一段步长和，就接到 `sb` 中，都算完后把 `sb` 转换为字符串重新赋给 `s` 继续判断</font>

#### AC代码

```
class Solution {
    public String digitSum(String s, int k) {
        while (s.length() > k) {
            int n = s.length();
            StringBuilder sb = new StringBuilder();
            for (int i = 0; i < n; i += k) {
                int sum = 0;
                for (int j = 0; j < k && i + j < n; j++) {
                    sum += s.charAt(i + j) - '0';
                }
                sb.append(sum);
            }
            s = sb.toString();
        }
        return s;
    }
}
```

#### 复杂度分析

- 时间复杂度：O(n^2)
- 空间复杂度：O(1)