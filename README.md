# next-node-in-tree
由满二叉树（除了最后一层）的正序遍历列表构建中序遍历，然后输出给定节点的下一节点

马蜂窝笔试算法B第一题：


    f=list(map(int,input().split()))
    n=len(f)
    p=int(input())
    class node():
        def __init__(self,x):
            self.val=x
            self.left=None
            self.right=None
    tree=node(f[0])
    ceng=[tree]
    for i in range(1,n):
        if not ceng[0].left:
            ceng[0].left=node(f[i])
            ceng.append(ceng[0].left)
        else:
            ceng[0].right=node(f[i])
            ceng.append(ceng[0].right)
            del ceng[0]
    res=[]
    def mid(tree):
        if tree:
            mid(tree.left)
            res.append(tree.val)
            mid(tree.right)
    mid(tree)
    print(res)
    for i in range(n):
        if res[i]==p:
            if i<n-1:
                print(res[i+1])
            else:
                print(-1)
            break
