#Binary Searh Tree (BST)
A **binary tree** has the following property for each node n(value: val):  

* n.val ≥ values in n’s left subtree  * n.val ≤ values in n’s right subtree

## Operations
### Search

```java
    public TreeNode iterativeSearch(TreeNode root, int value){
        TreeNode temp = root;
        while(null != temp && temp.val != value){
            if(temp.val < value){
                temp = temp.right;
            }else{
                temp = temp.left;
            }
        }
        return  temp;
    }

    public TreeNode recursiveSearch(TreeNode root, int value){

        if(null == root || root.val == value){
            return root;
        }

        if(root.val < value){
            return recursiveSearch(root.right, value);
        }else{
            return recursiveSearch(root.left, value);
        }
    }
```
### FindMin
```java
    public TreeNode minimum(TreeNode root){
        while(null != root.left){
            root = root.left;
        }
        return root;
    }
```
### FindMax
```java
    public TreeNode maximum(TreeNode root){
        while(null != root.right){
            root = root.right;
        }
        return root;
    }
```
### Successor
```java
    public TreeNode successor(TreeNode node){
        if(null != node.right){
            return minimum(node.right);
        }
        while (null != node.parent && node != node.parent.left){
            node = node.parent;
        }
        return node.parent;
    }
```
### In Order Traversal
```java
    public void traverseInOrder(TreeNode root){

    }
```

## Insert
```java
    public void insert(Tree T, TreeNode node){
        TreeNode y = null;
        TreeNode x = T.root;
        while(null != x){
            y = x;
            if(x.val < node.val){
                x = x.right;
            }else{
                x = x.left;
            }
        }
        node.parent = y;
        if(y.val < node.val){
            y.right = node;
        }else {
            y.left = node;
        }
    }
```

## Transplant
```java
    public void transplant(Tree tree, TreeNode u, TreeNode v){
        if(null == u.parent){ // u is the root
            tree.root = v;
        }else if(u == u.parent.left){
            u.parent.left = v;
        }else{
            u.parent.right = v;
        }
        if(null != v){
            v.parent = u.parent;
        }
    }
```

## Delete
```java
    public void delete(Tree tree, TreeNode node){
        if(null == node.left){ // has only right
            transplant(tree, node, node.right);
        }else if (null == node.right){ // has only left
            transplant(tree, node, node.left);
        }else{ //has left and right
            TreeNode y = minimum(node.right);
            if(y.parent != node){ // node.successor != node.right
            	   // y has no left definitely
                transplant(tree, y, y.right);
                //Wire the y to node as node.right
                y.right = node.right;
                y.right.parent = y;
            }
            transplant(tree, node, y);// node.successor == node.right
            //Wire the node.left to y as y.left
            y.left = node.left;
            node.left.parent = y;
        }
    }
```


[http://www.cnblogs.com/dongkuo/p/4868177.html](http://www.cnblogs.com/dongkuo/p/4868177.html)