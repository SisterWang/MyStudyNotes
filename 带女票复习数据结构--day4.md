# 带女票复习数据结构--day4

---

## 栈和队列

### 1.判断字符串序列是否为回文。（正读和反读都相同的字符序列为回文，如“abba”和“abcba”）
由于栈为先进后出，队列为先进先出。所以可以通过同时使用栈和队列的方法判断字符串序列的正读和反读是否一致。
```
int Palindrome_Test(){
    IniteStack(S);
    IniteQueue(Q);
    while((c=getchar) != '@'){
        Push(S,c);
        EnQueue(Q,c);
    }
    while(!StackEmpty(S)){
        Pop(S,a);
        DeQueue(Q,b);
        if(a!=b)
            return ERROR;
    }
    return OK;
}
```

## 树与二叉树

### 1.一颗具有n个结点的完全二叉树采用顺序结构，保存在数组SqBiTree中。用先序遍历访问该二叉树。
设二叉树的顺序存储表示如下：
```
#define Max_TREE_SIZE 100//最大节点数
typedef TElemType SqBiTree[Max_TREE_SIZE];//1号单元存储根节点
```
非遍历算法：
```
void PreOder_Sq(SqBiTree BT){
    InitStack(S);
    p=1;
    while( (p<n) || (!StackEmpty(S)) ){
        while(p<n){
            Visit(BT[p]);
            Push(S,p);
            p=p*2;
        }
        if(!StackEmpty(S)){
            Pop(S,p);
            p=p*2+1;
        }
    }
}
```

### 2.二叉树采用二叉链表存储，设计递归算法计算出二叉树中叶子节点的数目。
设二叉树的链表存储表示如下：
```
typedef struct BiTNode{
    TElemType data;
    struct BiTNode *lchild,*rchild;
}BiTNode,*BiTree;
```
递归算法：
```
int LeafCount_BiTree(BiTree T){
    if(!T)
        return 0;
    else{
        if(!T->lchild && !T->rchild)
            //数量加1
            return 1;
        else
            //向下查找当前节点的左右节点是否为树叶节点
            return LeafCount_BiTree(T->lchild) + LeafCount_BiTree(T->rchild);
    }
}
```