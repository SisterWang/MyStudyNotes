# 带女票复习数据结构--线性表and栈和队列
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
