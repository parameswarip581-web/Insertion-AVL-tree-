# Insertion-AVL-tree-
Practice program 
class Node:
    def __init__(self, key):
        self.key = key
        self.left = None
        self.right = None
        self.height = 1
def height(node):
    if not node:
        return 0
    return node.height
def getBalance(node):
    if not node:
        return 0
    return height(node.left) - height(node.right)
def rightRotate(y):
    x = y.left
    T2 = x.right
    x.right = y
    y.left = T2
    y.height = max(height(y.left), height(y.right)) + 1
    x.height = max(height(x.left), height(x.right)) + 1
    return x
def leftRotate(x):
    y = x.right
    T2 = y.left
    y.left = x
    x.right = T2
    x.height = max(height(x.left), height(x.right)) + 1
    y.height = max(height(y.left), height(y.right)) + 1
    return y
def insert(root, key):
    if not root:
        return Node(key)
    if key < root.key:
        root.left = insert(root.left, key)
    else:
        root.right = insert(root.right, key)
    root.height = 1 + max(height(root.left), height(root.right))
    balance = getBalance(root)
    if balance > 1 and key < root.left.key:
        return right Rotate(root)
    if balance < -1 and key > root.right.key:
        return leftRotate(root)
    if balance > 1 and key > root.left.key:
        root.left = leftRotate(root.left)
        return right Rotate(root)
    if balance < -1 and key < root.right.key:
        root.right = right Rotate(root.right)
        return leftRotate(root)
    return root
def inorder(root):
    if root:
        inorder(root.left)
        print root.key,
        inorder(root.right)
root = None
root = insert(root, 10)
OUTPUT:

AVL Tree (Inorder):
10 20 30 40 50
root = insert(root, 20)
root = insert(root, 30)
root = insert(root, 40)
root = insert(root, 50)
print "AVL Tree (Inorder):"
inorder(root)
