# LEETCODE-TREES-1325
```java
class Solution {
  public TreeNode removeLeafNodes(TreeNode root, int target) {
    if (root == null)
      return null;
    root.left = removeLeafNodes(root.left, target);
    root.right = removeLeafNodes(root.right, target);
    return isLeaf(root) && root.val == target ? null : root;
  }

  private boolean isLeaf(TreeNode root) {
    return root.left == null && root.right == null;
  }
}
```

Let's assume we have the following binary tree:

```
      1
     / \
    2   3
   /   / \
  2   2   4
 / 
2
```

And the target value to remove is `2`.

### Initial Call

We start by calling `removeLeafNodes(root, 2)` where `root` is the root of the tree with value `1`.

### Step-by-Step Execution

1. **Call**: `removeLeafNodes(root, 2)` where `root.val = 1`
   - The root is not `null`, so we proceed.
   - Recursively call `removeLeafNodes` on the left child (value `2`).

2. **Call**: `removeLeafNodes(root.left, 2)` where `root.left.val = 2`
   - The root is not `null`, so we proceed.
   - Recursively call `removeLeafNodes` on the left child (value `2`).

3. **Call**: `removeLeafNodes(root.left.left, 2)` where `root.left.left.val = 2`
   - The root is not `null`, so we proceed.
   - Recursively call `removeLeafNodes` on the left child (value `2`).

4. **Call**: `removeLeafNodes(root.left.left.left, 2)` where `root.left.left.left.val = 2`
   - The root is not `null`, so we proceed.
   - Recursively call `removeLeafNodes` on the left child which is `null`.

5. **Call**: `removeLeafNodes(root.left.left.left.left, 2)` where `root.left.left.left.left = null`
   - The root is `null`, return `null`.

6. **Return**: `null`
   - Recursively call `removeLeafNodes` on the right child which is `null`.

7. **Call**: `removeLeafNodes(root.left.left.left.right, 2)` where `root.left.left.left.right = null`
   - The root is `null`, return `null`.

8. **Return**: `null`
   - Now, check if the node with value `2` is a leaf and has the target value.
   - `isLeaf(root.left.left.left)` returns `true` because both children are `null`.
   - Since the node value is `2` (equal to target), return `null`.

9. **Return**: `null` (left child of `root.left.left` is removed)

10. **Continue Call**: `removeLeafNodes(root.left.left, 2)`
    - Recursively call `removeLeafNodes` on the right child which is `null`.

11. **Call**: `removeLeafNodes(root.left.left.right, 2)` where `root.left.left.right = null`
    - The root is `null`, return `null`.

12. **Return**: `null`
    - Now, check if the node with value `2` is a leaf and has the target value.
    - `isLeaf(root.left.left)` returns `true` because both children are `null`.
    - Since the node value is `2` (equal to target), return `null`.

13. **Return**: `null` (left child of `root.left` is removed)

14. **Continue Call**: `removeLeafNodes(root.left, 2)`
    - Recursively call `removeLeafNodes` on the right child which is `null`.

15. **Call**: `removeLeafNodes(root.left.right, 2)` where `root.left.right = null`
    - The root is `null`, return `null`.

16. **Return**: `null`
    - Now, check if the node with value `2` is a leaf and has the target value.
    - `isLeaf(root.left)` returns `true` because both children are `null`.
    - Since the node value is `2` (equal to target), return `null`.

17. **Return**: `null` (left child of root is removed)

18. **Continue Call**: `removeLeafNodes(root, 2)`
    - Recursively call `removeLeafNodes` on the right child (value `3`).

19. **Call**: `removeLeafNodes(root.right, 2)` where `root.right.val = 3`
    - The root is not `null`, so we proceed.
    - Recursively call `removeLeafNodes` on the left child (value `2`).

20. **Call**: `removeLeafNodes(root.right.left, 2)` where `root.right.left.val = 2`
    - The root is not `null`, so we proceed.
    - Recursively call `removeLeafNodes` on the left child which is `null`.

21. **Call**: `removeLeafNodes(root.right.left.left, 2)` where `root.right.left.left = null`
    - The root is `null`, return `null`.

22. **Return**: `null`
    - Recursively call `removeLeafNodes` on the right child which is `null`.

23. **Call**: `removeLeafNodes(root.right.left.right, 2)` where `root.right.left.right = null`
    - The root is `null`, return `null`.

24. **Return**: `null`
    - Now, check if the node with value `2` is a leaf and has the target value.
    - `isLeaf(root.right.left)` returns `true` because both children are `null`.
    - Since the node value is `2` (equal to target), return `null`.

25. **Return**: `null` (left child of `root.right` is removed)

26. **Continue Call**: `removeLeafNodes(root.right, 2)`
    - Recursively call `removeLeafNodes` on the right child (value `4`).

27. **Call**: `removeLeafNodes(root.right.right, 2)` where `root.right.right.val = 4`
    - The root is not `null`, so we proceed.
    - Recursively call `removeLeafNodes` on the left child which is `null`.

28. **Call**: `removeLeafNodes(root.right.right.left, 2)` where `root.right.right.left = null`
    - The root is `null`, return `null`.

29. **Return**: `null`
    - Recursively call `removeLeafNodes` on the right child which is `null`.

30. **Call**: `removeLeafNodes(root.right.right.right, 2)` where `root.right.right.right = null`
    - The root is `null`, return `null`.

31. **Return**: `null`
    - Now, check if the node with value `4` is a leaf and has the target value.
    - `isLeaf(root.right.right)` returns `true` because both children are `null`.
    - Since the node value is `4` (not equal to target), return `root.right.right`.

32. **Return**: `root.right.right` (value `4` remains)

33. **Continue Call**: `removeLeafNodes(root.right, 2)`
    - Now, check if the node with value `3` is a leaf and has the target value.
    - `isLeaf(root.right)` returns `false` because it has one child (value `4`).
    - Since the node value is `3` (not equal to target), return `root.right`.

34. **Return**: `root.right` (value `3` remains)

35. **Continue Call**: `removeLeafNodes(root, 2)`
    - Now, check if the node with value `1` is a leaf and has the target value.
    - `isLeaf(root)` returns `false` because it has one child (value `3`).
    - Since the node value is `1` (not equal to target), return `root`.

### Final Tree Structure

After all the recursive calls, the modified tree looks like this:

```
      1
       \
        3
         \
          4
```

All leaf nodes with value `2` have been removed.
