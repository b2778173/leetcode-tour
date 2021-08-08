# 145. Binary Tree Postorder Traversal

### Think: the order is Left--&gt;Right--&gt;Node, 剛好為preorder 的變形 N--&gt;R--&gt;L之reverse

### Steps:

1. 與prepost order 一樣, 但先改成left先入棧
2. 最後在reverse ans

```javascript
let ans = [];
let stack = [];
stack.push(root);
while(stack.length){
    let cur = stack.pop();
    ans.push(cur.val);
    if(cur){
        stack.push(cur.left);
        stack.push(cur.left);
    }
}
return ans.reverse(); // N-->R-->L --reverse--> L->R->N
```



