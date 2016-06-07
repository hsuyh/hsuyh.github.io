---
layout: post
title: Reverse string的實作
---

在leetcode #334 Reverse String的問題，在這裡記錄一下解法。

若是給你一個string＝"hello"，你要輸出"olleh"。

1. Iterative:
2. Recursive
3. Linked List


### Iterative
這個方法所需要的空間複雜度為 O(1)，每次你在移動字串時候，都需要一個temp來暫存。

```c
void reverseStringIterative(char *s)
{
  int len = strlen(s);
  char temp;

  for(int start=0, end=len-1; start<end; start++, end--)
  {
    temp = *(s+start);
    *(s+start) = *(s+end);
    *(s+end) = temp;
  }
}

```


### Recursive
這個方法比起Iterative來說，你必須不斷遞迴呼叫函數，處理速度會較慢，且都需要額外的暫存空間去儲存結果，空間複雜度為O(n)。

```c
void reverseStringRecursive(char *s, int start, int end)
{
  if(start<end)
  {
    char temp;
    temp = *(s+start);
    *(s+start) = *(s+end);
    *(s+end) = temp;
    reverseStringRecursive(s, start+1, end-1);
  }
}

```

### Circular Doubly Linked List
如果是在我們無法確認陣列大小的情況下，使用linked list 跟前兩個方法比較起來較為有彈性，不會有overflow或是記憶體閒置浪費的問題，但是他實作起來也比較複雜。 若是使用單向的linked list，我們需要一個一個pop來做reverse string，這樣會比較麻煩，所以使用雙向的linked list，透過鏈結的前後往返，來做到reverse。



```c

typedef struct character{
  char data;
  struct character *prev;
  struct character *next;
}CharData;

void reverseStringLinkedList(char *s)
{
  CharData *head=NULL;
  head = (struct character*)malloc(sizeof(CharData));
  head->prev = head;
  head->next = head;

  CharData *previous=head;
  CharData *current=NULL;

  for(int i=0;i<strlen(s);i++)
  {

    current = (struct character*)malloc(sizeof(CharData));
    current->data = *(s+i);

    current->prev = previous;
    previous->next = current;

    current->next = head;
    head->prev = current;

    previous = current;
  }

  for(int i=0;i<strlen(s);i++){
    *(s+i) = current->data;
    current = current->prev;
  }
}
```
