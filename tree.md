# 什么是树
    每棵树都有一个根节点
    每个节点有若干个子节点
    如果最多有2个节点,则称为二叉树;否则称为多叉树
## 二叉树节点的结构定义
	struct BinaryTreeNodeInner{
		int key;
		struct BinaryTreeNodeInner* left;
		struct BinaryTreeNodeInner* right;
	};
	typedef struct BinaryTreeNodeInner BinaryTreeNode;
## 遍历二叉树
	遍历方式：前序，中序，后序
	现在我将分别用递归(容易理解)和非递归(不会导致栈空间无限制增大)方式来实现它们。
#### 前序递归实现
	void preorder_recursive(BinaryTreeNode* root)
	{
		if(!root)
			return; 
		printf("%d ", root->key);
		preorder_recursive(root->left);
		preorder_recursive(root->right);
	}
#### 前序非递归实现(部分代码为伪代码)
	void preorder_iterative(BinaryTreeNode* root)
	{
		if(!root) return;
		st = 空栈(存储的元素为BinaryTreeNode*)
		st.push(root);
		while(!st.empty())
		{
			BinaryTreeNode* cur = st.pop();
			printf("%d ", cur->key);
		}
	}

    