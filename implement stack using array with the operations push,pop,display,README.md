y deva harsha
192311126
#include <stdio.h>
#define MAX_SIZE 10
int stack[MAX_SIZE];
int top = -1; 
int isEmpty() {
    if (top == -1)
        return 1;
    else
        return 0;
}
int isFull() {
    if (top == MAX_SIZE - 1)
        return 1;
    else
        return 0;
}
void push(int value) {
    if (isFull()) {
        printf("Stack overflow\n");
    } else {
        top = top + 1;
        stack[top] = value;
        printf("%d pushed to the stack\n", value);
    }
}
void pop() {
    if (isEmpty()) {
        printf("Stack underflow\n");
    } else {
        printf("Popped element: %d\n", stack[top]);
        top = top - 1;
    }
}
void display() {
    if (isEmpty()) {
        printf("Stack is empty\n");
    } else {
        printf("Stack elements: ");
        for (int i = top; i >= 0; --i) {
            printf("%d ", stack[i]);
        }
        printf("\n");
    }
}
int peek() {
    if (isEmpty()) {
        printf("Stack is empty\n");
        return -1;
    } else {
        return stack[top];
    }
}
int main() {
    push(10);
    push(20);
    push(30);
    display();
    pop();
    printf("Top element: %d\n", peek());
    display();
    return 0;
}
C:\Users\devah\Pictures\Screenshots\Screenshot 2023-12-29 134629.png
