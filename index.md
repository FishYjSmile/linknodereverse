### js链表翻转

/*function ListNode(x){
    this.val = x;
    this.next = null;
}*/
function ReverseList(pHead){
    var newHead, temp;
    if(!pHead){
        return null;
    }
    if(pHead.next === null){
        return pHead;    // 单递归参数为链尾时返回，
    } else {
        newHead = ReverseList(pHead.next);  // 进行递归，传递子链
    }
    temp = pHead.next;   // 交换指针位置
    temp.next = pHead;   // 此时为null以此不会出现对象地址相同
    pHead.next = null;     // 将首指针指向尾指针
    temp = null;              // 释放内存
    return newHead;        // 形成闭包，保存此时的链表对象
}
复制代码
例如  a -> b -> c -> d -> null 的形式进行翻转

此时先将此链表结构建好

function ListNode(x){
    this.val = x;
    this.next = null;
}
1.进行递归，分别传递的p 参数为 d   最终newp为d链表对象    ，并将该对象以闭包的方式保存

2.随后进行第二次递归 参数为 cd  最后进行 参数对象的交换 ， 其中通过指针第三项为null这个特性  ，temp = p -> next  (d)  , temp->next = p （ 此时的temp->next的值为null，所以可以直接赋值p对象，不会出现对象内存值相同） ,  p->next = null   (使链头其指向null)      

3.此时修改了参数链表的指向 ，又因为newp为闭包参数，所以前面改变的参数指向这里同时与newp指向的地址相同，所以也一起进行了修改，以此实现了翻转      

 out.
