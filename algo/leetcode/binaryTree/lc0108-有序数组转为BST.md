# 题目
https://leetcode.cn/problems/convert-sorted-array-to-binary-search-tree/
将有序数组转换为二叉搜索树

## 题意

给你一个整数数组 nums ，其中元素已经按 升序 排列，请你将其转换为一棵 高度平衡 二叉搜索树。
高度平衡 二叉树是一棵满足「每个节点的左右两个子树的高度差的绝对值不超过 1 」的二叉树。

![](./pict/lc0108-01.jpeg)

输入：nums = [-10,-3,0,5,9]
输出：[0,-3,9,-10,null,5]


## 思路

这个题是经典的二分法。

## 代码


```golang
func sortedArrayToBST(nums []int) *TreeNode {

    var arrayToBst   func (arr []int , left , right int ) *TreeNode

    arrayToBst =  func (arr []int , left , right int ) *TreeNode {
        if left > right {
            return nil 
        }

        mid := (left + right ) /2 

        node := &TreeNode{Val : arr[mid]}
        node.Left = arrayToBst(arr , left , mid -1) 
        node.Right =arrayToBst(arr , mid+1 , right) 

        return node 
    }

    root := arrayToBst(nums , 0 , len(nums) -1)
    return root 

}

```