y deva harsha
192311126
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

int countNodes(struct Node* head) {
    // Implementation goes here
}

int main() {
    struct Node* head = /* create linked list here */;

    int nodeCount = countNodes(head);
    printf("Number of nodes in the linked list: %d\n", nodeCount);

    return 0;
}
