# 带女票复习数据结构--day2
---

##线性表
###1.假设有两个按元素值递增有序排列的线性表La和Lb，均以单向链表作存储结构，请编写算法将La表和Lb表归并成一个按元素值递减有序排列的线性表Lc，并要求利用原表的空间节点构造Lc表。
本题目思想为按从小到大的顺序依次把La和Lb的元素插入到Lc的表头和其下一个元素之间，再处理剩余元素。
```
Status ListMergeOppose_L(LinkList &La,LinkList &Lb,LinkList &Lc){
    pa=La->next;
    pb=Lb->next;
    Lc=La;
    Lc->next = NULL;
    while(pb&&pa){
        if(pa->data<=pb->data){
            p=pa->next;
            pa->next=Lc->next;
            Lc->next=pa;
            pa=p;
        }
        else{
            p=pb->next;
            pb->next=Lc->next;
            Lc->next=pa;
            pb=p;
        }
    }
    while(pa){
        p=pa->next;
        pa->next=Lc->next;
        Lc->next=pa;
        pa=p;
    }
    while(pb){
        p=pb->next;
        pb->next=Lc->next;
        Lc->next=pb;
        pb=p;
    }
    free(Lb);
    return OK;
}
```
##栈
###1.假设一个算数表达式可以包含三种括号：圆括号“（”和“）”，方括号“[”和“]”，花括号“{”和“}”，且可以任意次序嵌套使用。已知表达式已存入数据元素为字符的顺序表中，编写判别给定表达式中所含括号是否正确配对出现的算法。
本题目使用一个栈S来判定将“（”、“[”、“{”入栈，当遇到“）”、“]”、“}”时，检查栈S是否空栈，若空栈，则返回表示不配对，否则判断栈顶元素是否为对应的“（”、“[”、“{”，若是则退栈，否则返回表示不配对。循环整个栈后判断是否空栈，若不是则返回表示不配对，否则配对成功。
```
Status Judge_Brackets(SqList Exp){
    InitStack(S);
    i=1;
    while(i<=Exp.length){
    switch(Exp.elem[i]){
        case(Exp.elem[i]=='('||Exp.elem[i]=='['||Exp.elem[i]=='{'):
            Push(S,Exp.elem[i]);
            break;
        case(Exp.elem[i]==')'):
            if(StackEmpty(S))
                return FALSE;
            else{
                Pop(S,ch);
                if(ch!='(')
                    return FALSE;
            }
        break;
        case(Exp.elem[i]==']'):
            if(StackEmpty(S))
                return FALSE;
            else{
                Pop(S,ch);
                if(ch!='[')
                    return FALSE;
            }
        break;
        case(Exp.elem[i]=='}'):
            if(StackEmpty(S))
                return FALSE;
            else{
                Pop(S,ch);
                if(ch!='{')
                    return FALSE;
            }
        break;
    }
    i++;
    }//while
    if(!StackEmpty(S))
        return FALSE;
    return OK;
}
```