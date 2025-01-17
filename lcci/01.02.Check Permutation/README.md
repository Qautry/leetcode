# [面试题 01.02. 判定是否互为字符重排](https://leetcode-cn.com/problems/check-permutation-lcci)

[English Version](/lcci/01.02.Check%20Permutation/README_EN.md)

## 题目描述

<!-- 这里写题目描述 -->
<p>给定两个字符串 <code>s1</code> 和 <code>s2</code>，请编写一个程序，确定其中一个字符串的字符重新排列后，能否变成另一个字符串。</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入:</strong> s1 = &quot;abc&quot;, s2 = &quot;bca&quot;
<strong>输出:</strong> true
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入:</strong> s1 = &quot;abc&quot;, s2 = &quot;bad&quot;
<strong>输出:</strong> false
</pre>

<p><strong>说明：</strong></p>

<ul>
	<li><code>0 &lt;= len(s1) &lt;= 100 </code></li>
	<li><code>0 &lt;= len(s2) &lt;= 100 </code></li>
</ul>

## 解法

<!-- 这里可写通用的实现逻辑 -->

用一个哈希表作为字符计数器，`O(n)` 时间内解决。

<!-- tabs:start -->

### **Python3**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```python
class Solution:
    def CheckPermutation(self, s1: str, s2: str) -> bool:
        n1, n2 = len(s1), len(s2)
        if n1 != n2:
            return False
        counter = Counter()
        for i in range(n1):
            counter[s1[i]] += 1
            counter[s2[i]] -= 1
        return all(v == 0 for v in counter.values())
```

### **Java**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```java
class Solution {
    public boolean CheckPermutation(String s1, String s2) {
        int n1 = s1.length();
        int n2 = s2.length();
        if (n1 != n2) {
            return false;
        }
        int[] counter = new int[128];
        for (int i = 0; i < n1; ++i) {
            ++counter[s1.charAt(i)];
            --counter[s2.charAt(i)];
        }
        for (int v : counter) {
            if (v != 0) {
                return false;
            }
        }
        return true;
    }
}
```

### **JavaScript**

```js
var CheckPermutation = function (s1, s2) {
    let n1 = s1.length,
        n2 = s2.length;
    if (n1 != n2) return false;
    let counter = {};
    for (let i = 0; i < n1; i++) {
        let cur1 = s1.charAt(i),
            cur2 = s2.charAt(i);
        counter[cur1] = (counter[cur1] || 0) + 1;
        counter[cur2] = (counter[cur2] || 0) - 1;
    }
    return Object.values(counter).every(v => v == 0);
};
```

### **Go**

```go
func CheckPermutation(s1 string, s2 string) bool {
	freq := make(map[rune]int)
	for _, r := range s1 {
		freq[r]++
	}
	for _, r := range s2 {
		if freq[r] == 0 {
			return false
		}
		freq[r]--
	}
	for _, v := range freq {
		if v != 0 {
			return false
		}
	}
	return true
}
```

### **C++**

```cpp
class Solution {
public:
    bool CheckPermutation(string s1, string s2) {
        int n1 = s1.size();
        int n2 = s2.size();
        if (n1 != n2) return 0;
        vector<int> counter(128);
        for (int i = 0; i < n1; ++i)
        {
            ++counter[s1[i]];
            --counter[s2[i]];
        }
        for (int v : counter)
            if (v) return 0;
        return 1;
    }
};
```

### **...**

```

```

<!-- tabs:end -->
