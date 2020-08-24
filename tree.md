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
			if(cur->left)
			{
				st.push(cur->left);
			}
			if(cur->right)
			{
				st.push(cur->right);
			}
		}
	}
#### 中序递归实现
	void inorder_recursive(BinaryTreeNode* root)
	{
		if(!root)
			return; 
		inorder_recursive(root->left);
		printf("%d ", root->key);
		inorder_recursive(root->right);
	}

#### 中序非递归实现(部分代码为伪代码)
	void inorder_iterative(BinaryTreeNode* root)
	{
		if(!root)
			return;
		ls1 = 空链表(存储的元素为BinaryTreeNode*)
		ls2 = 空链表(存储的元素为ls1第一个元素的位置)
		ls1.push_back(root)
		ls2.push_back(ls1的第一个位置)
		while(!ls2.empty())
		{
			location = ls2.pop_front()
			node = 在location上的值
			if node.left is not null
				在ls1的location之前插入node.left,并且将新元素的位置插入ls2
			if node.right is not null
				在ls1的location之后插入node.right,并且将新元素的位置插入ls2
		}
		for node in ls1
		{
			printf("%d ", node->key);
		}
		
	}
#### 后序递归实现
	void postorder_recursive(BinaryTreeNode* root)
	{
		if(!root)
			return; 
		printf("%d ", root->key);
		postorder_recursive(root->left);
		postorder_recursive(root->right);
	}
#### 后序非递归实现
	void postorder_iterative(BinaryTreeNode* root)
	{
		if(!root)
			return;
		ls1 = 空链表(存储的元素为BinaryTreeNode*)
		ls2 = 空链表(存储的元素为ls1第一个元素的位置)
		ls1.push_back(root)
		ls2.push_back(ls1的第一个位置)
		while(!ls2.empty())
		{
			location = ls2.pop_front()
			node = 在location上的值
			if node.right is not null
				在ls1的location之前插入node.right,并且将新元素的位置插入ls2,location也更新为该位置
			if node.left is not null
				在ls1的location之前插入node.left,并且将新元素的位置插入ls2
		}
		for node in ls1
		{
			printf("%d ", node->key);
		}
		
	}
####层序遍历
	如果需要从树的根部一层层从左往右遍历，应该怎么实现？
####ZigZag层序遍历
	如果需要从树的根部一层层 先从左往右 然后从右往左 方向依次交替遍历，应该怎么实现？
## 思考题
	前面介绍的3种非递归遍历，有办法提升性能吗？
    