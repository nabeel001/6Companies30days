Question Link: [https://www.geeksforgeeks.org/problems/delete-n-nodes-after-m-nodes-of-a-linked-list](https://www.geeksforgeeks.org/problems/delete-n-nodes-after-m-nodes-of-a-linked-list)

```cpp
 Node* linkdelete(Node* head, int n, int m) {
        // code here
        Node* node = head;
        while(node!=nullptr)
        {
            Node* prev = nullptr;
            // Skip m nodes
            for(size_t id=0; id<m && node!=nullptr; id++)
            {
                prev = node;
                node = node->next;
            }
            
            // Delete n nodes
            for(size_t id=0; id<n && node!=nullptr; id++)
            {
                Node* temp = node;
                node = node->next;
                delete temp;
            }
            prev->next = node;
        }
        return head;
    }
```
