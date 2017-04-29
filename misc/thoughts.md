**MacQ:**

1.line function

2.remove empty char from a string

**SqPoint:**

1.find duplicated int

\(1\)set \(2\)math \(3\)manual hash

2.multithreading

**Schat:**

1.pascal

\(1\)recursive \(2\)hash \(3\)duplicates
**BB:**
1.changesToMakeAnagram
2.isBST

```

// This is the text editor interface. 
// Anything you type or change here will be seen by the other person in real time.

//                 5
//            3        8
//        1      6   7    9  



struct Node {
    Node* left;
    Node* right;
    int val;
};

bool checkSubTree(Node* n, int min, int max){
    if(n==NULL) return true;
    
    return (n->val < max && n->val > min) && 
            checkSubTree(n->left,min,n->val) &&
            checkSubTree(n->right,n->val,max);
}

bool isBST(Node* n) {
    checkSubTree(n,INT_MIN,INT_MAX);
}
```

