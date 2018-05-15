# 带女票复习数据结构--day3

---

## 栈和队列

### 1.对逆波兰表达式求值
逆波兰表达式是一种十分有用的表达式，它将复杂表达式转换为可以依靠简单的操作得到计算结果的表达式。例如(a+b)*(c+d)转换为ab+cd+*  
**运算方式：**  
如果当前字符为变量或者为数字，则压栈，如果是运算符，则将栈顶两个元素弹出作相应运算，结果再入栈，最后当表达式扫描完后，栈里的就是结果。

```
OperandType CalVal_InverPoland(SqList Exp_b){
    InitStack(OPND);
    j=0;
    while(j<=Exp_b.Length-1){
        if(!In(Exp_b.elem[j],OP))//OP为运算符集，此句话为判断是否为运算符
            Push(OPND,Exp_b.elem[j]);//数字入栈
        else{
            Pop(OPND,b);
            Pop(OPND,a);//弹出栈顶的两个元素
            theta=Exp_b.elem[j];//取出运算符
            Push(OPND,Operate[a,theta,b]);//运算后将结果入栈
        }
        j++;
    }//while
    Pop(OPND,e);//栈中最后剩余的就是结果
    return e;
}
```

### 2.设计求杨辉三角形某一项值的递归算法。
杨辉三角：  
![image](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0d/PascalTriangleAnimated2.gif/210px-PascalTriangleAnimated2.gif)  
由上图可见：杨辉三角形的顶端和边缘（左边或右边）的值为1，而中间部分的值为它左上方和右上方元素值的和（即第row行第col列的元素值等于第row-1行、col-1列的值加上第row-1行、col列的值。）

```
int Yanghui(int row,int col){//row为行,col为列。
    if(col == 1 || row ==col){//第一列或最后一列
        return 1;
    }
    else{
        return(Yanghui(row-1,col-1) + Yanghui(row-1,col))
    }//中间部分的值为它左上方和右上方元素值的和
}
```

### 3.假设以带头结点的循环列表表示队列，并且只设一个指针指向队尾元素节点（注意不设头指针），试编写相应的队列初始化、入队列和出队列算法。
只设一个指针Q.rear指向队尾元素节点，存储结构的描述与单链队列一致。  
**队列初始化：**  

```
Status InitCircleQueue(LinkQueue &Q){
    Q.rear=(QueuePtr)malloc(sizeof(QNode));//申请空间，并用Q.rear指向
    if(!Q.rear)
        exit(OVERFLOW);
    Q.rear->next=Q.rear;
    return OK;
}//队列初始化
```
**入队列：**  

```
Status EnCircleQueue(LinkQueue &Q,QElemType e){//把元素e插入队尾
    p=(QueuePtr)malloc(sizeof(QNode));
    if(!p)
        exit(OVERFLOW);
    p->data=e;
    p->next=Q.rear->next;//把p放在Q.rare后面
    Q.rear->next=p;
    Q.rear=p;//修改尾指针
    return OK;
}
```
**出队列：**  

```
Status DeCircleQueue(LinkQueue &Q,QElemType e){//把元素e从队头删除
    if(Q.rear->next=Q.rear)//队列已空
        return INFEASIBLE;
    p=Q.rear->next->next;
    e=p->data;
    Q.rare->next->next=p->next;
    if(Q.rear==p)//队列只有一个元素的情况
        Q.rear=p->next;
    free(p);
    return OK;
}
```

