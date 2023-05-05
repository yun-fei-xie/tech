# Rabin-karp算法

## 算法思想

BF 算法的时候讲过，如果模式串长度为 m，主串长度为 n，那在主串中，就会有 n-m+1 个长度为 m 的子串，我们只需要暴力地对比这 n-m+1 个子串与模式串，就可以找出主串与模式串匹配的子串。但是，每次检查主串与子串是否匹配，需要依次比对每个字符，所以 BF 算法的时间复杂度就比较高，是 O(n*m)。

对朴素的字符串匹配算法稍加改造，引入哈希算法，时间复杂度立刻就会降低。RK 算法的思路是这样的：我们通过哈希算法对主串中的 n-m+1 个子串分别求哈希值，然后逐个与模式串的哈希值比较大小。如果某个子串的哈希值与模式串相等，那就说明对应的子串和模式串匹配了（这里先不考虑哈希冲突的问题，后面我们会讲到）。因为哈希值是一个数字，数字之间比较是否相等是非常快速的，所以模式串和子串比较的效率就提高了。


不过在实际生产中，设计一个可以应对各种类型字符的哈希算法并不简单。

## 算法实现

### 滚动hash

rsync文件传输协议中使用这个方法。





### 快速幂



### 代码

用这个方法解答leetcode https://leetcode.cn/problems/find-the-index-of-the-first-occurrence-in-a-string/description/

给你两个字符串 haystack 和 needle ，请你在 haystack 字符串中找出 needle 字符串的第一个匹配项的下标（下标从 0 开始）。如果 needle 不是 haystack 的一部分，则返回  -1 。

示例 1：

输入：haystack = "sadbutsad", needle = "sad"
输出：0
解释："sad" 在下标 0 和 6 处匹配。
第一个匹配项的下标是 0 ，所以返回 0 。
示例 2：

输入：haystack = "leetcode", needle = "leeto"
输出：-1
解释："leeto" 没有在 "leetcode" 中出现，所以返回 -1 。


这份代码没有实现滚动hash，而是朴素hash。
```go

func strStr(haystack string, needle string) int {

	m := len(haystack)
	n := len(needle)
	patternHash := hashEncode(needle)
	for i := 0; i <= (m - n); i++ {
		//text中的每个子串为：text[i:n+i]
		if hashEncode(haystack[i:n+i]) == patternHash {
			return i
		}
	}

	return -1
}

/*
hashEncode [a...z]->[0...25]编码
*/
func hashEncode(s string) int {
	var h int
	for i := 0; i < len(s); i++ {
		h = h*26 + int(s[i]-'a')
	}
	return h
}

```





