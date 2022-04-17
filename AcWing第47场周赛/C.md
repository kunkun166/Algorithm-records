##### 2022/4/17

### 数字母

[https://www.acwing.com/problem/content/4402/](https://www.acwing.com/problem/content/4402/)

### 题目描述

<font size=2> 给定一个仅包含小写字母的集合，请你判断集合中不同字母的数量。</font>

<font size=2> **输入格式**<br>输入一行字符串，用以描述这个小写字母集合。字符串以 `{` 开始，以 `}` 结束，中间列出所有集合中包含的小写字母，小写字母两两之间用逗号 `,` 加空格 `` 隔开。</font>

<font size=2> **输出格式**<br>一个整数，表示集合中不同字母的数量。
</font>

<font size=2> **数据范围**<br>前5个测试点满足，集合中包含的字母数量在 [0,10] 范围内。<br>所有测试点满足，集合中包含的字母数量在 [0,333] 范围内。
</font>

<font size=2> **输入样例1：**</font>

```
{a, b, c}
```

<font size=2> **输出样例1：**</font>

```
3
```

<font size=2> **输入样例2：**</font>

```
{b, a, b, a}
```

<font size=2> **输出样例2：**</font>

```
2
```

<font size=2> **输入样例3：**</font>

```
{}
```

<font size=2> **输出样例3：**</font>

```
0
```

### 题解

#### 方法一

- <font size=2>这道题考察了Java中对字符串处理的熟悉程度</font>

- <font size=2>做法就是挨个扫描每个字符，如果是小写字母就加入到HashSet中，利用HashSet的无序且不重复性即可得到答案，即set.size()</font>

#### AC代码

```
public class Main {
    public static void main(String[] args) throws IOException {
        Scanner sc = new Scanner(System.in);
        String str = sc.nextLine();
        char[] ch = str.toCharArray();
        HashSet<Character> set = new HashSet<>();
        for (int i = 1; i < ch.length - 1; i++) {
            if (ch[i] >= 'a' && ch[i] <= 'z') {
                set.add(ch[i]);
            }
        }
        System.out.print(set.size());
    }
}
```

#### 复杂度分析

- 时间复杂度：O(n)，n是字符串的长度
- 空间复杂度：O(n)，需要将字符串转为字符数组
