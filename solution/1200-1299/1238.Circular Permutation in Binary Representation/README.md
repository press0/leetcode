# [1238. 循环码排列](https://leetcode.cn/problems/circular-permutation-in-binary-representation)

[English Version](/solution/1200-1299/1238.Circular%20Permutation%20in%20Binary%20Representation/README_EN.md)

## 题目描述

<!-- 这里写题目描述 -->

<p>给你两个整数&nbsp;<code>n</code> 和 <code>start</code>。你的任务是返回任意 <code>(0,1,2,,...,2^n-1)</code> 的排列 <code>p</code>，并且满足：</p>

<ul>
	<li><code>p[0] = start</code></li>
	<li><code>p[i]</code> 和 <code>p[i+1]</code>&nbsp;的二进制表示形式只有一位不同</li>
	<li><code>p[0]</code> 和 <code>p[2^n -1]</code>&nbsp;的二进制表示形式也只有一位不同</li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>n = 2, start = 3
<strong>输出：</strong>[3,2,0,1]
<strong>解释：</strong>这个排列的二进制表示是 (11,10,00,01)
     所有的相邻元素都有一位是不同的，另一个有效的排列是 [3,1,0,2]
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输出：</strong>n = 3, start = 2
<strong>输出：</strong>[2,6,7,5,4,0,1,3]
<strong>解释：</strong>这个排列的二进制表示是 (010,110,111,101,100,000,001,011)
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 16</code></li>
	<li><code>0 &lt;= start&nbsp;&lt;&nbsp;2^n</code></li>
</ul>

## 解法

<!-- 这里可写通用的实现逻辑 -->

<!-- tabs:start -->

### **Python3**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```python
class Solution:
    def circularPermutation(self, n: int, start: int) -> List[int]:
        g = [i ^ (i >> 1) for i in range(1 << n)]
        j = g.index(start)
        return g[j:] + g[:j]
```

```python
class Solution:
    def circularPermutation(self, n: int, start: int) -> List[int]:
        return [i ^ (i >> 1) ^ start for i in range(1 << n)]
```

### **Java**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```java
class Solution {
    public List<Integer> circularPermutation(int n, int start) {
        int[] g = new int[1 << n];
        int j = 0;
        for (int i = 0; i < 1 << n; ++i) {
            g[i] = i ^ (i >> 1);
            if (g[i] == start) {
                j = i;
            }
        }
        List<Integer> ans = new ArrayList<>();
        for (int i = j; i < j + (1 << n); ++i) {
            ans.add(g[i % (1 << n)]);
        }
        return ans;
    }
}
```

```java
class Solution {
    public List<Integer> circularPermutation(int n, int start) {
        List<Integer> ans = new ArrayList<>();
        for (int i = 0; i < 1 << n; ++i) {
            ans.add(i ^ (i >> 1) ^ start);
        }
        return ans;
    }
}
```

### **C++**

```cpp
class Solution {
public:
    vector<int> circularPermutation(int n, int start) {
        int g[1 << n];
        int j = 0;
        for (int i = 0; i < 1 << n; ++i) {
            g[i] = i ^ (i >> 1);
            if (g[i] == start) {
                j = i;
            }
        }
        vector<int> ans;
        for (int i = j; i < j + (1 << n); ++i) {
            ans.push_back(g[i % (1 << n)]);
        }
        return ans;
    }
};
```

```cpp
class Solution {
public:
    vector<int> circularPermutation(int n, int start) {
        vector<int> ans(1 << n);
        for (int i = 0; i < 1 << n; ++i) {
            ans[i] = i ^ (i >> 1) ^ start;
        }
        return ans;
    }
};
```

### **Go**

```go
func circularPermutation(n int, start int) []int {
	g := make([]int, 1<<n)
	j := 0
	for i := range g {
		g[i] = i ^ (i >> 1)
		if g[i] == start {
			j = i
		}
	}
	return append(g[j:], g[:j]...)
}
```

```go
func circularPermutation(n int, start int) (ans []int) {
	for i := 0; i < 1<<n; i++ {
		ans = append(ans, i^(i>>1)^start)
	}
	return
}
```

### **...**

```

```

<!-- tabs:end -->
