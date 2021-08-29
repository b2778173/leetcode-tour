---
description: >-
  Given two integer arrays preorder and inorder where preorder is the preorder
  traversal of a binary tree and inorder is the inorder traversal of the same
  tree, construct and return the binary tree.
---

# 105. Construct Binary Tree from Preorder and Inorder Traversal

![Input: preorder = \[3,9,20,15,7\], inorder = \[9,3,15,20,7\] Output: \[3,9,20,null,null,15,7\]](../.gitbook/assets/image%20%2818%29.png)

### Think

1. preoder 的第一個為root node
2. inorder root左為左子樹, 右為右子樹
3. preorder從左邊開始,先碰到的先放入

### Step:

1. 以hashMap記住inorder 的index , value
2. 呼叫helper 放入inorderStartIndex,  inorderEndIndex, preOrderStartIndex, preOrderEndIndex
3. is, ie, ps , pe隨cur root node變動, 關係如下:

```javascript
    int[] pre;
    HashMap<Integer, Integer> memo = new HashMap<>();
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        for(int i = 0 ; i < inorder.length ; i++){
            memo.put(inorder[i], i);
        }
        pre = preorder;
        
        return helper(0, inorder.length-1, 0, preorder.length-1);
    }
    
    public TreeNode helper(int is, int ie, int ps, int pe) {
        if( pe < ps) return null; // 左邊總是先進行, 如果寫 ie < is || pe < ps 會在左邊觸底後就停止, 導致p 沒走完
        int root = pre[ps];
        int ri = memo.get(root);
        
        TreeNode newRoot = new TreeNode(root); 
        newRoot.left = helper(is, ri - 1, ps+1, ri-is+ps);
        newRoot.right = helper(ri+1, ie, ps-is+ri+1, pe);
        return newRoot;
    }
```

