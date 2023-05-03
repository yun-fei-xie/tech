# Brute Force算法

暴力匹配算法在leetcode上有一道题，找出字符串中第一个匹配项的下标。

https://leetcode.cn/problems/find-the-index-of-the-first-occurrence-in-a-string/



```go 

func strStr(haystack string, needle string) int {

	m := len(haystack)
	n := len(needle)

	for i := 0; i <= (m - n); i++ { // 枚举haystack字符串中的每一个可能的起始点i (i<=(m-n) 可以提前退出)
		// 每一轮模式串都从0开始，文本串从i开始
		hStartIndex := i
		nStartIndex := 0

		for nStartIndex < n && haystack[hStartIndex] == needle[nStartIndex] {
			hStartIndex++
			nStartIndex++
		}
		if nStartIndex == n {
			return i
		}
	}

	return -1
}

```

